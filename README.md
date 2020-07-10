# autodrive
A python implementation for Advanced Driving Assistant. (Now with GPU Support)

![autodrive output sample](https://github.com/ajeetkharel/autodrive/blob/master/outputs/output_sample.png)

## About the model
This model can:
  * Detect lane lines and fit a curve on them with a polynomial mask.
  * Detect objects like: cars, buses, persons, traffic lights, etc

### How to run the model?

* Firstly, clone the repository and change the directory to it.
* Run the following command inside ``` autodrive ``` directory in the terminal/command prompt.
```bash
python main.py
```
NOTE: This is a default run type for this model which uses the input video stored in ``` test_videos ``` folder.

#### To test the algorithm on your own video type the following command:
```bash
python main.py --input {path to the video}
```
#### And, if you want to store the model's output on the video then specify the output video name as:
```bash
python main.py --output {a file name.mkv}
```
NOTE: The output video file's extension must be ``` .mkv```.

## New Features
* Added GPU support to run object detection using cuda support for getting higher FPS
###Usage:
```bash
	python main.py -g  # -g for GPU
```
   	NOTE: The -g inclusion while running the model will allow the model to use GPU for faster inference and higher FPS

* Added support for using TINY YOLO Model to perform even more faster detection with smaller model.
###Usage:
```bash
	python main.py -t  # -t for TINY
```
   	NOTE: The -t inclusion while running the model will tell the model to use TINY Yolo model for running object detection.

## Extra features of the model
You can also make changes inside the code to add more features in the models' output.Like:

* To add labels in the top of every bounding box, pass a argument named ``` labels=True ``` in ```pipeline ``` function of [main.py](https://github.com/ajeetkharel/autodrive/blob/master/main.py)
  ```python
  if not lane_only:
			self.lane_mask_final = self.object_detector.draw_boxes(self.frame, self.lane_mask_final, labels=True)
  ```
 
 * If you only want to mask and detect the lanes and dont want to detect objects, you can make ```lane_only``` argument in [main.py](https://github.com/ajeetkharel/autodrive/blob/master/main.py) to ```True```
 
 ```python
 if __name__=='__main__':
   ...
	#run the pipeline on specified video
	pipeline.run_video(input_video, output_video, lane_only=True)
   ...
 ```
 
## Authors

* **Amit Kharel** - *Overall works* - [ajeetkharel](https://github.com/ajeetkharel)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

[![Kofi](https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/b5278db5-d08d-44ae-8a27-e3a827c411c3/dcgc1gs-0e20e8ea-65aa-4224-b802-18d4346b8efe.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3sicGF0aCI6IlwvZlwvYjUyNzhkYjUtZDA4ZC00NGFlLThhMjctZTNhODI3YzQxMWMzXC9kY2djMWdzLTBlMjBlOGVhLTY1YWEtNDIyNC1iODAyLTE4ZDQzNDZiOGVmZS5wbmcifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6ZmlsZS5kb3dubG9hZCJdfQ.dzvTPy1MvnZdNJLcv7FGClYdpW9rYptsJGpnzzvL8iQ)](https://ko-fi.com/ajeetkharel)
