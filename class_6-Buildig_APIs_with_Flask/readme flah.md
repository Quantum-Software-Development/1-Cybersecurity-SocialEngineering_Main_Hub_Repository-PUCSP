<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# retre todas a streferencias de file

```md
# Class 6 — Cybersecurity and Social Engineering / Building APIs

> Complete repository for class 6 focused on **Cybersecurity**, **Social Engineering**, and **Building APIs with Flask**, combining theory, practical examples, accessible explanations, and Python code inspired by the provided material.

## About

Study and practice material on the fundamentals of APIs, REST architecture, JSON, Flask routes, query string parameters, and spreadsheet integration with Pandas, plus complementary discussions about cybersecurity and social engineering for both beginners and professionals.

## Suggested repository name

`class-6-cybersecurity-social-engineering-building-apis`

## Suggested short repo description

Class 6 on Cybersecurity, Social Engineering, and building APIs with Flask, including concepts, practical examples, query strings, JSON, Excel integration via Pandas, and key notes about localhost, IPs, and running outside Colab.

## Hashtags / Topics

`python` `flask` `api` `rest-api` `json` `pandas` `cybersecurity` `social-engineering` `networking` `localhost` `query-string` `excel` `data-science` `jupyter` `puc-sp`

---

# Table of Contents

- [1. Overview](#1-overview)
- [2. Class goals](#2-class-goals)
- [3. Cybersecurity and social engineering concepts](#3-cybersecurity-and-social-engineering-concepts)
- [4. What is an API](#4-what-is-an-api)
- [5. SOA and REST](#5-soa-and-rest)
- [6. What is JSON](#6-what-is-json)
- [7. Flask and its role in this class](#7-flask-and-its-role-in-this-class)
- [8. Why not use Flask in Colab](#8-why-not-use-flask-in-colab)
- [9. Localhost, local IP, and 127.0.0.1](#9-localhost-local-ip-and-127001)
- [10. Ping 127.0.0.1](#10-ping-127001)
- [11. Public IP, private IP, dynamic IP, fixed IP](#11-public-ip-private-ip-dynamic-ip-fixed-ip)
- [12. What is a query string](#12-what-is-a-query-string)
- [13. The role of ? in the URL](#13-the-role-of--in-the-url)
- [14. URL encoding and special characters](#14-url-encoding-and-special-characters)
- [15. What “default” means in code](#15-what-default-means-in-code)
- [16. Structure of the Flask examples](#16-structure-of-the-flask-examples)
- [17. Example 1 — first API](#17-example-1--first-api)
- [18. Example 2 — endpoint /dados](#18-example-2--endpoint-dados)
- [19. Example 3 — parameter in the route](#19-example-3--parameter-in-the-route)
- [20. Example 4 — sum with query string](#20-example-4--sum-with-query-string)
- [21. Example 5 — returning Excel as JSON](#21-example-5--returning-excel-as-json)
- [22. Example 6 — filter by drug](#22-example-6--filter-by-drug)
- [23. Professional improvements to the code](#23-professional-improvements-to-the-code)
- [24. Relationship between APIs and security](#24-relationship-between-apis-and-security)
- [25. Social engineering in the API context](#25-social-engineering-in-the-api-context)
- [26. Best practices](#26-best-practices)
- [27. Suggested project structure](#27-suggested-project-structure)
- [28. Full Python code](#28-full-python-code)
- [29. Technical wrap‑up of the class](#29-technical-wrapup-of-the-class)
- [30. References](#30-references)

---

# 1. Overview

This class introduces how to build APIs with Python and Flask, starting from basic ideas like API, REST, JSON, routes, parameters, and JSON responses, and moving toward practical use with an Excel spreadsheet and Pandas.

As a complement, this material ties the technical content to **Cybersecurity** and **Social Engineering**, because any system exposed over a network must consider security, data exposure, authentication, endpoint abuse, and human manipulation risks.

---

# 2. Class goals

- Understand what an API is and why it matters.
- Learn core REST and JSON concepts.
- Create routes with Flask.
- Work with route and query string parameters.
- Read Excel data with Pandas and return JSON.
- Relate API construction to security and social engineering.

---

# 3. Cybersecurity and social engineering concepts

**Cybersecurity** is the field that protects systems, networks, applications, and data against unauthorized access, attacks, leaks, interruptions, and malicious manipulation.

**Social Engineering** is the manipulation of people to gain access, information, or privileges, often without attacking the technology first. In API environments, attackers may trick users, analysts, or admins into revealing credentials, tokens, internal URLs, or sensitive data.

In simple terms: securing an API is not only about the code, but also about people, processes, and how the system is deployed and used.

---

# 4. What is an API

API stands for **Application Programming Interface**. It is a set of definitions and protocols used to build and integrate applications, so different products and services can communicate without knowing each other’s internal implementation.

For beginners, you can imagine an API as a “waiter” between systems: one side sends a request, the other does the work, and the API organizes the conversation. For professionals, the API is a formal communication contract between client and service.

---

# 5. SOA and REST

**SOA** (Service Oriented Architecture) is a distributed system style in which services cooperate to implement functionalities, emphasizing interoperability, dynamic discovery, and separation of business and presentation logic.

**REST** (Representational State Transfer), defined by Roy Fielding in 2000, is based on principles such as client–server, statelessness, cache, layered system, code-on-demand, and uniform interface.

When we create endpoints like `/dados`, `/farmacia`, or `/remedio`, we are following REST‑like ideas: exposing resources via clear URLs, usually accessed over HTTP.

---

# 6. What is JSON

**JSON** is a lightweight data‑interchange format, easy for humans to read and write, and easy for machines to parse and generate. It is text‑based, language‑independent, and heavily used in APIs.

JSON usually organizes data into:
- key–value pairs, like objects;
- ordered lists, like arrays.

Example:

```json
{
  "name": "Fab",
  "course": "Data Science",
  "active": true
}
```

When the pharmacy API returns the spreadsheet as JSON, it converts tabular data into a standard structure that other applications can consume.

---

# 7. Flask and its role in this class

**Flask** is a Python microframework used to build web apps and APIs with straightforward syntax. In this class it’s used to create HTTP routes such as `/`, `/dados`, `/dobrar/<num>`, `/somar`, `/farmacia`, and `/remedio`.

It’s a good teaching tool because it makes the essentials very visible:

- app creation;
- route definition;
- parameter handling;
- returning text or JSON;
- running locally on port 5000.

---

# 8. Why not use Flask in Colab

**Flask should not be used as the main environment on Google Colab for this type of class**, because Colab is primarily designed for notebook execution, not for hosting a local web server in the same way as a user’s own machine. This limitation makes it harder to test stable local routes, access the server consistently, and reproduce the typical local development workflow.

Even when Flask seems to start inside a notebook, the natural way to use it is to run locally and access `127.0.0.1:5000` in your browser, with full control over network, ports, and environment.

In practice:

- on a local machine, you fully control the server process;
- on Colab, you are in a remote, temporary environment;
- this breaks the natural flow of testing localhost APIs and inspecting traffic as in real development.

For Flask, recommended environments are:

- local JupyterLab;
- VS Code or similar IDE;
- a local terminal with Python;
- a local virtual environment.

---

# 9. Localhost, local IP, and 127.0.0.1

The Flask server is published locally on port 5000, commonly accessed at `127.0.0.1:5000`.

**127.0.0.1** is the loopback address, known as **localhost**. It refers to the same machine on which the program is running. When you access `http://127.0.0.1:5000`, your own computer is talking to the server it is running.

For beginners, it’s like knocking on your own door to see if someone answers. Technically, it’s a logical loopback interface used to test and use the local network stack.

---

# 10. Ping 127.0.0.1

The address `127.0.0.1` is traditionally used to test the local networking stack. Running `ping 127.0.0.1` checks whether the loopback interface responds, which helps confirm that the basic local TCP/IP stack is functioning.

If `ping 127.0.0.1` fails, it does not directly mean “no internet,” but rather that some local networking component, firewall, or system configuration is broken or restricted. This test targets the local machine, not the external internet.

### If ping fails, what to do

1. Recheck the command: `ping 127.0.0.1`.
2. Try `ping localhost`.
3. Restart the network interface or the machine.
4. Inspect firewall and security tools.
5. Check the OS TCP/IP stack configuration.
6. In corporate or institutional environments, contact IT support to review drivers, policies, and network services.

---

# 11. Public IP, private IP, dynamic IP, fixed IP

## Public IP

Address visible on the public internet, typically assigned by an ISP to your router or network edge device. Many devices at home can share this single public IP.

## Private IP

Address used inside the local network (home, school, office, lab), like `192.168.x.x` or `10.x.x.x`. It identifies devices inside the LAN, not on the public internet.

## Dynamic IP

A dynamic IP changes over time, which is common at home routers. The ISP may renew or change this address periodically.

## Fixed IP

A fixed (static) IP is kept constant, often used by companies, institutions, or servers that must always be reachable at the same address.

In simple terms:

- private IP = internal address;
- public IP = external address;
- dynamic IP = can change;
- fixed IP = stays the same.

---

# 12. What is a query string

Example 4 implements a sum using parameters passed via **query string**, like `127.0.0.1:5000/somar?n1=10&n2=90`.

A **query string** is the portion of the URL used to send parameters after the main path. It’s commonly used for filters, search, pagination, and simple API operations.

Example in a browser:

```text
http://127.0.0.1:5000/somar?n1=10&n2=90
```

Here:

- `/somar` is the endpoint;
- `?` starts the query string;
- `n1=10` is the first parameter;
- `&n2=90` adds another one.

---

# 13. The role of ? in the URL

The `?` symbol marks the **start of the query string**.

In other words:

- before `?` is the resource path;
- after `?` come the request parameters.

Examples:

```text
http://127.0.0.1:5000/remedio?cod=C108
http://127.0.0.1:5000/somar?n1=10&n2=90
http://site.com/search?product=notebook&brand=acer
```


---

# 14. URL encoding and special characters

When a URL has spaces, accents, or special characters in parameters, **URL encoding** is needed. It converts problematic characters into a safe representation that can travel inside a URL.

Examples:

- a space becomes `%20` or sometimes `+`;
- characters like `ç`, `ã`, `é` are encoded according to UTF‑8 rules.

Example parameter:

```text
name=João da Silva
```

Encoded:

```text
name=Jo%C3%A3o%20da%20Silva
```

Without proper encoding, parameters might arrive corrupted or misinterpreted by the server.

---

# 15. What “default” means in code

In the doubling example, the function can be defined with a default parameter, such as `num=0`, so there is a fallback value if none is provided.

**Default** means a fallback value. If no value is passed, the code uses this default to avoid errors or to define a predictable behavior.

Example:

```python
def double(num=0):
    return num * 2
```

In query string handling, this pattern is common:

```python
request.args.get("n1", default=0, type=float)
```

If `n1` is not present in the URL, `0` is used instead.

---

# 16. Structure of the Flask examples

The examples share a common structure:

- import Flask;
- create the app;
- define routes with `@app.route`;
- implement response functions;
- run the server with `app.run(...)`.

The server typically uses `0.0.0.0` on port `5000`, which exposes the HTTP service on the local machine.

---

# 17. Example 1 — first API

The first example returns a simple message at the root route `/`.

### Code

```python
from flask import Flask
import os

app = Flask(__name__)

@app.route("/", methods=["GET"])
def index():
    return "Resposta da API!! V1.0"

if __name__ == "__main__":
    app.run(host=os.getenv("IP", "0.0.0.0"), port=int(os.getenv("PORT", 5000)))
```


### Explanation

This is a minimal API:

- `Flask(__name__)` creates the app;
- `@app.route("/")` defines the home route;
- the function returns plain text;
- `app.run(...)` starts the local server.

---

# 18. Example 2 — endpoint /dados

The second example adds `/dados`, returning simple student data.

### Code

```python
from flask import Flask
import os

app = Flask(__name__)

@app.route("/", methods=["GET"])
def index():
    return "Resposta da API!! V2.0"

@app.route("/dados", methods=["GET"])
def dados():
    return "RA0021, NOME:SAVINO"

if __name__ == "__main__":
    app.run(host=os.getenv("IP", "0.0.0.0"), port=int(os.getenv("PORT", 5000)))
```


### Explanation

The API exposes:

- `/` as the home endpoint;
- `/dados` as a data endpoint.

Each route maps to a function and response.

---

# 19. Example 3 — parameter in the route

Example 3 creates `/dobrar/<num>`, where the number is part of the path.

### Code

```python
from flask import Flask
import os

app = Flask(__name__)

@app.route("/", methods=["GET"])
def index():
    return "Resposta da API!! V3.0"

@app.route("/dados", methods=["GET"])
def dados():
    return "RA0021, NOME:SAVINO"

@app.route("/dobrar/<num>", methods=["GET"])
def get_dobro(num=0):
    dobro = 2 * float(num)
    return f"Dobro {dobro}"

if __name__ == "__main__":
    app.run(host=os.getenv("IP", "0.0.0.0"), port=int(os.getenv("PORT", 5000)))
```


### Explanation

The value after `/dobrar/` is passed as `num`:

- the function converts it to `float`;
- calculates the double;
- returns the result as text.

---

# 20. Example 4 — sum with query string

Example 4 uses a query string to receive two numbers and return their sum.

### Code

```python
from flask import Flask, request
import os

app = Flask(__name__)

@app.route("/", methods=["GET"])
def index():
    return "Resposta da API!! V4.0"

@app.route("/dados", methods=["GET"])
def dados():
    return "RA0021, NOME:SAVINO"

@app.route("/dobrar/<num>", methods=["GET"])
def get_dobro(num=0):
    dobro = 2 * float(num)
    return f"Dobro {dobro}"

@app.route("/somar", methods=["GET"])
def somar():
    n1 = float(request.args.get("n1"))
    n2 = float(request.args.get("n2"))
    soma = n1 + n2
    return f"Soma {soma}"

if __name__ == "__main__":
    app.run(host=os.getenv("IP", "0.0.0.0"), port=int(os.getenv("PORT", 5000)))
```


### Improved version with default

```python
@app.route("/somar", methods=["GET"])
def somar():
    n1 = request.args.get("n1", default=0, type=float)
    n2 = request.args.get("n2", default=0, type=float)
    soma = n1 + n2
    return f"Soma {soma}"
```


### Explanation

`request.args` reads parameters from the query string. Using `default=0` avoids errors when a parameter is missing.

---

# 21. Example 5 — returning Excel as JSON

Example 5 reads `Farmacia.xlsx` with Pandas and returns it as JSON at `/farmacia`.

### Code

```python
import pandas as pd
from flask import Flask, Response
import os

dataFrame = pd.read_excel("Farmacia.xlsx")

app = Flask(__name__)

@app.route("/farmacia", methods=["GET"])
def get_farmacia():
    return Response(
        dataFrame.to_json(orient="records"),
        mimetype="application/json"
    )

if __name__ == "__main__":
    app.run(host=os.getenv("IP", "0.0.0.0"), port=int(os.getenv("PORT", 5000)))
```


### Explanation

This example connects:

- Excel data;
- Pandas processing;
- publishing as a JSON API.

Other systems can consume the spreadsheet without manually opening Excel.

---

# 22. Example 6 — filter by drug

Example 6 adds `/remedio`, which receives `cod` via query string and filters the DataFrame.

### Code

```python
import pandas as pd
from flask import Flask, request, Response
import os

dataFrame = pd.read_excel("Farmacia.xlsx")

app = Flask(__name__)

@app.route("/farmacia", methods=["GET"])
def get_farmacia():
    return Response(
        dataFrame.to_json(orient="records"),
        mimetype="application/json"
    )

@app.route("/remedio", methods=["GET"])
def get_remedio():
    cod = request.args.get("cod")
    prod = dataFrame.loc[dataFrame["Codigo"] == cod]
    return Response(
        prod.to_json(orient="records"),
        mimetype="application/json"
    )

if __name__ == "__main__":
    app.run(host=os.getenv("IP", "0.0.0.0"), port=int(os.getenv("PORT", 5000)))
```


### Explanation

The API now supports:

- full dataset (`/farmacia`);
- filtered dataset by code (`/remedio?cod=...`).

This pattern is common in real‑world APIs.

---

# 23. Professional improvements to the code

The didactic examples can be improved for robustness and clarity by:

- validating inputs;
- handling errors;
- consistently returning JSON;
- using clear messages and HTTP status codes.

Improved sample:

```python
import os
import pandas as pd
from flask import Flask, request, jsonify, Response

app = Flask(__name__)

EXCEL_FILE = "Farmacia.xlsx"

try:
    df = pd.read_excel(EXCEL_FILE)
    load_error = None
except Exception as e:
    df = pd.DataFrame()
    load_error = str(e)


@app.route("/", methods=["GET"])
def home():
    return jsonify({
        "message": "API for Class 6 - Building APIs with Flask",
        "status": "online"
    })


@app.route("/dados", methods=["GET"])
def dados():
    return jsonify({
        "ra": "RA0021",
        "name": "SAVINO"
    })


@app.route("/dobrar/<num>", methods=["GET"])
def double(num):
    try:
        value = float(num)
        return jsonify({
            "input": value,
            "double": value * 2
        })
    except ValueError:
        return jsonify({
            "error": "Invalid parameter. Example: /dobrar/100"
        }), 400


@app.route("/somar", methods=["GET"])
def sum_route():
    n1 = request.args.get("n1", default=None, type=float)
    n2 = request.args.get("n2", default=None, type=float)

    if n1 is None or n2 is None:
        return jsonify({
            "error": "Send n1 and n2 via query string. Example: /somar?n1=10&n2=20"
        }), 400

    return jsonify({
        "n1": n1,
        "n2": n2,
        "sum": n1 + n2
    })


@app.route("/farmacia", methods=["GET"])
def farmacia():
    if load_error:
        return jsonify({
            "error": "Failed to load spreadsheet",
            "details": load_error
        }), 500

    return Response(
        df.to_json(orient="records", force_ascii=False),
        mimetype="application/json"
    )


@app.route("/remedio", methods=["GET"])
def remedio():
    if load_error:
        return jsonify({
            "error": "Failed to load spreadsheet",
            "details": load_error
        }), 500

    cod = request.args.get("cod", default=None, type=str)

    if not cod:
        return jsonify({
            "error": "Provide medicine code via query string. Example: /remedio?cod=C108"
        }), 400

    filtered = df.loc[df["Codigo"] == cod]

    if filtered.empty:
        return jsonify({
            "message": "No records found for the given code",
            "code": cod
        }), 404

    return Response(
        filtered.to_json(orient="records", force_ascii=False),
        mimetype="application/json"
    )


if __name__ == "__main__":
    app.run(
        host=os.getenv("IP", "0.0.0.0"),
        port=int(os.getenv("PORT", 5000)),
        debug=False
    )
```


---

# 24. Relationship between APIs and security

Whenever you build an API, security concerns appear, such as:

- excessive data exposure;
- missing authentication;
- malicious parameters;
- endpoint enumeration;
- automated abuse;
- leaking sensitive information in responses.

Even in local, introductory examples, each route that responds to a browser is exposing behavior and data. In production this requires access control, input validation, logging, rate limiting, and careful handling of sensitive information.

---

# 25. Social engineering in the API context

In the API context, social engineering can happen when someone:

- urgently asks for environment credentials;
- persuades a colleague to reveal tokens or keys;
- sends fake documentation links;
- requests “quick tests” on internal endpoints;
- impersonates technical staff to gain access.

This shows that API security is not only about Flask or Python code: it also depends on how people manage secrets, share information, and validate identity.

---

# 26. Best practices

- Use Flask to learn and prototype local APIs.
- First test on `127.0.0.1:5000`, the classic local setup.
- Prefer running locally instead of in Colab for this class.
- Validate all inputs from routes and query strings.
- Use sensible defaults where appropriate.
- Return JSON consistently, with clear messages.
- Do not expose unnecessary data.
- Document endpoints clearly.
- Protect credentials, tokens, and real‑world spreadsheets.
- Always consider the human factor in security.

---

# 27. Suggested project structure

```text
class-6-cybersecurity-social-engineering-building-apis/
│
├── README.md
├── app.py
├── requirements.txt
├── Farmacia.xlsx
└── notebooks/
    └── AULA05_CONSTRUINDO_API.pdf
```


---

# 28. Full Python code

```python
import os
import pandas as pd
from flask import Flask, request, jsonify, Response

app = Flask(__name__)

EXCEL_FILE = "Farmacia.xlsx"

try:
    df = pd.read_excel(EXCEL_FILE)
    load_error = None
except Exception as e:
    df = pd.DataFrame()
    load_error = str(e)


@app.route("/", methods=["GET"])
def index():
    return jsonify({
        "message": "API response!!",
        "status": "online",
        "description": "Study API for Class 6 - Building APIs with Flask"
    })


@app.route("/dados", methods=["GET"])
def dados():
    return jsonify({
        "ra": "RA0021",
        "name": "SAVINO"
    })


@app.route("/dobrar/<num>", methods=["GET"])
def get_double(num):
    try:
        value = float(num)
        return jsonify({
            "input": value,
            "double": value * 2
        })
    except ValueError:
        return jsonify({
            "error": "Invalid parameter. Use a number in the route, e.g. /dobrar/100"
        }), 400


@app.route("/somar", methods=["GET"])
def sum_numbers():
    n1 = request.args.get("n1", default=0, type=float)
    n2 = request.args.get("n2", default=0, type=float)

    return jsonify({
        "n1": n1,
        "n2": n2,
        "sum": n1 + n2,
        "note": "Values were received via query string."
    })


@app.route("/farmacia", methods=["GET"])
def get_farmacia():
    if load_error:
        return jsonify({
            "error": "Failed to load spreadsheet.",
            "details": load_error
        }), 500

    return Response(
        df.to_json(orient="records", force_ascii=False),
        mimetype="application/json"
    )


@app.route("/remedio", methods=["GET"])
def get_remedio():
    if load_error:
        return jsonify({
            "error": "Failed to load spreadsheet.",
            "details": load_error
        }), 500

    cod = request.args.get("cod", default=None, type=str)

    if not cod:
        return jsonify({
            "error": "Provide the medicine code via query string. Example: /remedio?cod=C108"
        }), 400

    prod = df.loc[df["Codigo"] == cod]

    if prod.empty:
        return jsonify({
            "message": "No medicine found for the provided code.",
            "code": cod
        }), 404

    return Response(
        prod.to_json(orient="records", force_ascii=False),
        mimetype="application/json"
    )


@app.route("/health", methods=["GET"])
def health():
    return jsonify({
        "api": "ok",
        "excel_loaded": load_error is None,
        "localhost_example": "Use http://127.0.0.1:5000/"
    })


if __name__ == "__main__":
    app.run(
        host=os.getenv("IP", "0.0.0.0"),
        port=int(os.getenv("PORT", 5000)),
        debug=False
    )
```


---

# 29. Technical wrap‑up of the class

The class progressively shows how to go from a single route to a full API that reads an Excel spreadsheet and serves it as JSON, using Flask, query strings, and Pandas.

By connecting this to cybersecurity and social engineering, we learn that building an API is not only about making endpoints work, but also about understanding exposure, validation, secure data handling, and human‑driven risks.

---

# 30. References

- GOMES, Eduardo Savino. **Construindo uma API**. Course material, PUC‑SP.
- JSON.org. **Introducing JSON**.
- FIELDING, Roy. **Architectural Styles and the Design of Network-based Software Architectures**.

---
## Important note about Flask on Colab

**It is not recommended to use Flask on Google Colab as the main development environment for this class**, because Flask’s natural workflow depends on local execution, local ports, and testing via `localhost/127.0.0.1`, while Colab is a remote, temporary notebook environment. This makes API testing less predictable and less faithful to a real local development scenario.

---
## Quick query string examples in a browser

```text
http://127.0.0.1:5000/somar?n1=10&n2=90
http://127.0.0.1:5000/remedio?cod=C108
http://127.0.0.1:5000/search?name=Joao%20Silva
```

- `?` = start of the query string.
- `&` = separates parameters.
- `%20` = encoded space.

---
## Requirements.txt

```txt
flask
pandas
openpyxl
```

```
```

