# The API Log Parser

#### ##

Duration: 90 minutes  
File: (https://github.com/growexx/public_documents/blob/main/api_logs.txt)  
This test requires candidates to write a function to process complex, structured data.

---

## 1. The Task

Create a function **`analyze_api_logs(log_data)`** that reads an **`api_logs.txt`** file as input and returns a structured summary object (dictionary/JSON).

---

## 2. The Log Data Format

Each log entry is a string containing several key-value pairs separated by pipes (`|`).  
The pairs can appear in any order, and their values are essential for analysis.

| Key  | Example Data | Description |
|------|---------------|-------------|
| **UID**  | `UID:XYZ-789` | Unique User Identifier (string) |
| **TIME** | `TIME:1678886405` | Unix Epoch Timestamp (integer) |
| **STAT** | `STAT:200`, `STAT:404` | HTTP status code (integer) |
| **PATH** | `PATH:/auth/token` | The API endpoint (string) |
| **SIZE** | `SIZE:1024b`, `SIZE:0b` | Response payload size (must be parsed to an integer) |
| **MSG**  | `MSG:Auth Failed` | Optional message, present only on errors |

---

### Input File (https://github.com/growexx/public_documents/blob/main/api_logs.txt)


    "UID:A1 | TIME:1678886400 | PATH:/data/v1 | STAT:200 | SIZE:1024b",

    "STAT:401 | PATH:/auth/token | TIME:1678886405 | UID:B2 | SIZE:0b | MSG:Auth Failed",

    "SIZE:2048b | TIME:1678886410 | STAT:200 | PATH:/data/v1 | UID:C3",

    "UID:D4 | PATH:/data/v2 | STAT:404 | TIME:1678886415 | SIZE:10b",

    "TIME:1678886420 | STAT:500 | PATH:/data/v1 | UID:E5 | SIZE:12b | MSG:Server Crash",

    "STAT:401 | UID:F6 | SIZE:0b | PATH:/auth/token | TIME:1678886425"


---

### 3. Required Output Logic
The function must calculate the following metrics and organize errors as specified.

3.1 Summary Metrics

1. total_requests – Total number of log entries processed.

2. success_count – Total requests with STAT:200.

3. error_count – Total requests with STAT:4xx or STAT:5xx.

4. max_payload_size_bytes – The single largest SIZE value across all logs, converted to a pure integer byte count.

3.2 Organized Errors
The function must generate a nested structure of errors, first grouped by Endpoint (PATH) and then by Status Code (STAT).

Structure:

1. Outer key -> The PATH string

2. Inner key -> The STAT code string (e.g., "401")

3. Value -> Count of how many times that specific status code occurred for that specific path

4. Expected Output Structure (for the Sample Input)


{

  "summary": {

    "total\_requests": 6,

    "success\_count": 2,

    "error\_count": 4,

    "max\_payload\_size\_bytes": 2048

  },

  "errors\_by\_path": {

    "/auth/token": {

      "401": 2

    },

    "/data/v2": {

      "404": 1

    },

    "/data/v1": {

      "500": 1

    }

  }

}
