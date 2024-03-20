1. Clone the [Musika](https://github.com/marcoppasini/musika) here and rename it to "repo".
2. Open a terminal and run `docker compose up --build -d`
3. Enter the running container with an interactve bash shell `docker-compose exec musika-notebook /bin/bash`
4. Once inside the container's bash shell, run `python musika_test.py` 

Notes:
1. To ensure that the Gradio app is accessible from outside the Docker container, you need to make sure that iface.launch() (located in utils.py) is called with the `server_name='0.0.0.0'` argument. This will make the Gradio server listen on all network interfaces inside the container, allowing external access through the mapped port.
```python
print("CLICK ON LINK BELOW TO OPEN GRADIO INTERFACE")
if train:
    if self.args.share_gradio:
        iface.launch(prevent_thread_lock=True, share=True, server_name='0.0.0.0')
    else:
        iface.launch(prevent_thread_lock=True, server_name='0.0.0.0')
else:
    if self.args.share_gradio:
        iface.launch(share=True, server_name='0.0.0.0')
    else:
        iface.launch(server_name='0.0.0.0')
```
2. See [here](https://huggingface.co/musika) for model checkpoints.