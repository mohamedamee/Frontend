<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Coding Assistant</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to right, #e3f2fd, #ffffff);
            margin: 0;
            padding: 20px;
            color: #333;
        }
        header {
            text-align: center;
            margin-bottom: 30px;
            background-color: #4A90E2;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: white;
            font-size: 2em;
            margin: 0;
        }
        .container {
            max-width: 800px;
            margin: 20px auto;
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }
        label {
            display: block;
            margin: 15px 0 5px;
            font-weight: bold;
            font-size: 1.1em;
        }
        input[type="text"], select, button {
            display: block;
            width: 100%;
            padding: 12px;
            margin: 10px 0 20px;
            font-size: 1em;
            border: 1px solid #ccc;
            border-radius: 6px;
            transition: all 0.3s ease;
        }
        input[type="text"]:focus, select:focus, button:focus {
            border-color: #4A90E2;
            box-shadow: 0 0 8px rgba(74, 144, 226, 0.2);
            outline: none;
        }
        button {
            background-color: #4A90E2;
            color: white;
            cursor: pointer;
            border: none;
            text-transform: uppercase;
            font-weight: bold;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #357ABD;
        }
        h2 {
            margin-top: 40px;
            color: #333;
            font-size: 1.4em;
            border-bottom: 2px solid #4A90E2;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
        pre {
            background-color: #f4f4f4;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: auto;
            white-space: pre-wrap;
            font-size: 0.95em;
        }
        ul {
            list-style-type: none;
            padding: 0;
            margin-top: 20px;
        }
        li {
            padding: 15px;
            background: #f9f9f9;
            border: 1px solid #ddd;
            border-radius: 8px;
            margin-bottom: 10px;
            transition: background-color 0.3s ease;
        }
        li:hover {
            background-color: #f0f4f8;
        }
        .history {
            max-height: 200px;
            overflow-y: auto;
            margin-top: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 10px;
            background: #f9f9f9;
        }
        .history::-webkit-scrollbar {
            width: 8px;
        }
        .history::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        .history::-webkit-scrollbar-thumb {
            background: #4A90E2;
            border-radius: 8px;
        }
        .history::-webkit-scrollbar-thumb:hover {
            background: #357ABD;
        }
        .explanation-checkbox {
            display: flex;
            align-items: center;
            margin: 10px 0;
        }
        .explanation-checkbox input {
            margin-right: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Coding Assistant</h1>
    </header>

    <div class="container">
        <form action="/generateCode" method="post">
            <label for="problem">Problem Statement:</label>
            <input type="text" id="problem" name="problem" placeholder="Describe your coding problem here..." required>

            <label for="language">Programming Language:</label>
            <select id="language" name="language">
                <option value="Java">Java</option>
                <option value="Python">Python</option>
                <option value="C">C</option>
                <option value="C++">C++</option>
                <option value="JavaScript">JavaScript</option>
                <option value="Go">Go</option>
            </select>

            <div class="explanation-checkbox">
                <input type="checkbox" id="explain" name="explain">
                <label for="explain">Include explanation</label>
            </div>

            <button type="submit">Generate Code</button>
        </form>

        <h2>Generated Code:</h2>
        <pre th:text="${code}">
/* Example Snippets:
Java:
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}

Python:
def greet():
    print("Hello, World!")
greet()

JavaScript:
function greet() {
    console.log("Hello, World!");
}
greet();
*/
        </pre>

        <h2>History:</h2>
        <div class="history">
            <ul>
                <li th:each="item : ${history}" th:text="${item}">Previous generated code snippets will appear here...</li>
            </ul>
        </div>
    </div>
</body>
</html>
