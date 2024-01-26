# Cog DensePose
This is a [Cog wrapper](https://github.com/replicate/cog) for the [Detectron2](https://github.com/facebookresearch/detectron2) version of [DensePose](https://github.com/facebookresearch/detectron2/tree/main/projects/DensePose)

For a command line version of the same thing, try [vid2densepose](https://github.com/Flode-Labs/vid2densepose) by @Flode-Labs

## Setup
Make sure you have Docker installed.
Install cog
```
sudo curl -o /usr/local/bin/cog -L https://github.com/replicate/cog/releases/latest/download/cog_`uname -s`_`uname -m`
sudo chmod +x /usr/local/bin/cog
```

Build
```
cog build
```

## Predict
Here are the inputs you need for prediction: 
1. Image or video file 
2. DensePose model from the list of models in predict.py (optional)
3. Overlay (optional)
4. Visualizer (optional)

```
cog predict -i input=@dorothy.jpg
```
## To build an image and start a server
Build the image
```
cog build -t <name>
```
Run a prediction on the image
```
cog predict <name> -i input=@<img or video file path>
```
Start a server
```
docker run -d --rm -p 5000:5000 <name>
```
Make a prediction with the server
```
curl http://localhost:5000/predictions -X POST \
    -H 'Content-Type: application/json' \
    -d '{"input": {"input": <string link to image>}}'

```