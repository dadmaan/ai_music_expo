# Running Musika with Docker

1. Clone the [Musika](https://github.com/marcoppasini/musika) here and rename it to "repo".
2. Open a terminal and run `docker compose up --build -d`
3. You can access the Gradio interface on `localhost:7861` on your browser

#### If you want to run and test other scripts of the Musika
1. Enter the running container with an interactve bash shell `docker-compose exec musika-notebook /bin/bash`
2. Once inside the container's bash shell, run for example `python musika_train.py` to train the model.  

Notes:
1. To ensure that the Gradio app is accessible from outside the Docker container, you need to make sure that iface.launch() (located in utils.py) is called with the `server_name='0.0.0.0'` argument. This will make the Gradio server listen on all network interfaces inside the container, allowing external access through the mapped port.
```python
print("CLICK ON LINK BELOW TO OPEN GRADIO INTERFACE")
if train:
    if self.args.share_gradio:
        iface.launch(prevent_thread_lock=True, share=True, server_name='0.0.0.0', server_port=7861)
    else:
        iface.launch(prevent_thread_lock=True, server_name='0.0.0.0', server_port=7861)
else:
    if self.args.share_gradio:
        iface.launch(share=True, server_name='0.0.0.0', server_port=7861)
    else:
        iface.launch(server_name='0.0.0.0', server_port=7861)
```
2. See [here](https://huggingface.co/musika) for model checkpoints.
