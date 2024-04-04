# Running Microsoft Muzic projects locally

1. Clone the [Muzic](https://github.com/microsoft/muzic/tree/main) here and rename it to "repo".
2. Open a terminal and run `docker compose up --build -d`
3. You can access the Jupyter notebook on `localhost:8888` on your browser.


### Notes:
1. They were some depency issues regarding `numpy`, `scipy`, `protobuf` and `sklearn` packages that are fixed in the requirements file in the parent folder.
