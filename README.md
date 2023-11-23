#  Weakly Annotated Video Landmarks (WAVL) dataset

In order to mimic a keyframe dataset from videos which contain landmark information we merged images from two different sources: the ["Google Landmarks v2 dataset"](https://github.com/cvdfoundation/google-landmark) and the ["Vimeo Creative Commons Collection (V3C1)"](https://catalog.data.gov/dataset/vimeo-creative-commons-collection-v3c1) video dataset.These combined sources allowed us to create a dataset that contains sets of keyframes as they would be extracted from one video, containing both keyframes of a particular landmark as well as unrelated keyframes (noise).
For each set of keyframes representing a video, we combined on average 30 associated images from the Google Landmarks v2 dataset with in average 11 keyframes (noise images) from one of the videos in the V3C1 dataset. This process has been done for 141 landmarks.

In addition, we perform a targeted web search for relevant landmark training images. Recognizing that web data can introduce considerable noise, we filtered out some of the images by a algorithm which is described in []().


## Organisation of the dataset

The repository does not contain any content, but provides links or relative path information to images and videos from the downloaded Google Landmarks v2 and the V3C1 datasets.

For the Google Landmarks v2 dataset you have to download the first 50 of the provided TAR files. The link of the first of these TAR files is [https://s3.amazonaws.com/google-landmark/train/images_000.tar](https://s3.amazonaws.com/google-landmark/train/images_000.tar). And similarly for the other files. 
The specifid image path information is related to the root directory where these TAR files are extraced.

From the V3C1 dataste at least the first 5269 videos have to be downloaded.


A list of used landmarks can be found in ```landmarks_WAVL.txt```.

The used images and video frames for each landmark are described in ```images_WAVL.json```.
For each landmark the selected images from Google Landmarks v2 dataset and the video frames from the V3C1 dataset are specified.
The landmark_id and the category specification are taken from the Google Landmarks v2 dataset:
Example for the landmark "Pont du Gard":
```json
{
    "Pont du Gard": {
        "google_v2_images": {
            "landmark_id": "199507",
            "category": "http://commons.wikimedia.org/wiki/Category:Pont_du_Gard",
            "image_files": [
                "0\\0\\0\\00019b859b575233.jpg",
                "0\\0\\a\\00a5552acdff3c1b.jpg",
				....
            ]
        },
        "V3C1_images": {
            "video_file": "V3C1\\videos\\00048\\00048.mp4",
            "frame_positions": [
                1250,
                1875,
				...
            ]
        }
    },
	....
}
```

The JSON description of the web images in the file ```internet_images_WAVL.json``` containes a list of image links for each landmark. Additionaly for each image it is specified if it has been filtered out ("filtered": true) or not ("filtered": false):
Example for the landmark "Pont du Gard":
```json
{
    "Pont du Gard": [
        {
            "image_url": "https://i.pinimg.com/originals/18/1a/f8/181af8a72831026b18091e244b89fdfa.jpg",
            "filtered": false
        },
		....
	]
	...
}
```
