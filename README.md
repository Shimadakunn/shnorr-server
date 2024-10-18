# Schnorr Proof Server

This project demonstrates a Schnorr proof system implementation, including a secure server and a vulnerable server for educational purposes. It also includes an exploit script to demonstrate the vulnerability in the insecure implementation.

## Project Structure

- `schnorr_server.py`: Secure implementation of the Schnorr proof server
- `schnorr_server_vuln.py`: Vulnerable implementation of the Schnorr proof server
- `exploit_schnorr_server_vuln.py`: Script to exploit the vulnerability in the insecure server
- `requirements.txt`: List of Python dependencies
- `Dockerfile`: For containerizing the secure server

## Setup

- Docker

  - Install Docker Desktop from [here](https://www.docker.com/products/docker-desktop/)
  - Run the docker daemon
    ```
    docker build -t schnorr-server .
    ```
  - Run the docker CLI

    ```
    docker run -p 5001:5001 schnorr-server

    ```

- Python

  - Install the required dependencies:

  ```
  pip install -r requirements.txt
  ```

  - Start the Schnorr server:

  ```
  python schnorr_server.py
  ```

## Generate Schnorr Proof

```
curl http://localhost:5001/schnorr-proof
```

This return a json response with proofs

## Challenge

```
curl -X POST http://localhost:5000/verify-proof -H "Content-Type: application/json" -d '{"r": <valeur_r>, "e": <valeur_e>, "s": <valeur_s>, "y": <valeur_y>, "g": <valeur_g>, "p": <valeur_p>}'
```

this returns the result of the challenge you submitted

## Exploit vulnerability

Start the vulnerable server

```
python schnorr_server_vuln.py
```

Run the exploit script

```
python exploit_schnorr_server_vuln.py
```
