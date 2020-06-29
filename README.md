# Serverless Image Tag Processor
Based off of https://github.com/RaghavPrabhu/Deep-Learning/tree/master/serverless_image_tensorflow/backend_api but tuned for easy for AWS SAM deployment.

Just a simple API endpoint that returns the "tags" for an image. Uses TensorFlow and mobilenet.

### To Deploy
- `git clone https://github.com/davidkryzaniak/serverless-image-tag-processor`
- `cd serverless-image-tag-processor`
- `npm install`
- `sam deploy --guided`

The API Gateway that is created will be in the displayed in the sam deploy output. Base64 encode your JPG image (current limitation) and POST it in the body of the request to your new endpoint.

## Results
<a href="https://www.flickr.com/photos/dave_kz/28223945764/in/datetaken/"><img src="https://live.staticflickr.com/8860/28223945764_abcf711503_z.jpg" width="640" height="427" alt="IMSA SportsCar Championship race at Road America"></a>
```JSON 
{
  "result":[
    {"className":"racer, race car, racing car","probability":0.9504339694976807},
    {"className":"sports car, sport car","probability":0.028354940935969353},
    {"className":"ambulance","probability":0.018328115344047546}
  ]
}
```

<a href="https://www.flickr.com/photos/dave_kz/21075440363/in/datetaken/" title="Seattle Aquarium"><img src="https://live.staticflickr.com/5681/21075440363_20453a1f28_z.jpg" width="640" height="427" alt="Seattle Aquarium"></a>
```JSON 
{
  "result":[
    {"className":"anemone fish","probability":0.9829691052436829},
    {"className":"sea anemone, anemone","probability":0.016800260171294212},
    {"className":"coral reef","probability":0.00014219412696547806}
  ]
}
```

<a href="https://www.flickr.com/photos/dave_kz/21507090770/in/datetaken/" title="Port of Seattle"><img src="https://live.staticflickr.com/5633/21507090770_49e79bb186_z.jpg" width="640" height="427" alt="Port of Seattle"></a>
```JSON 
{
  "result":[
    {"className":"fireboat","probability":0.9550132751464844},
    {"className":"dock, dockage, docking facility","probability":0.03869175910949707},
    {"className":"liner, ocean liner","probability":0.002760218223556876}
  ]
}
```
