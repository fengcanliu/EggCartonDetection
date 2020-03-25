1. Convert xml label to csv

    `python xml_to_csv.py`
    
2. Generate the TFRecord files by issuing these commands from the \object_detection folder:

``python generate_tfrecord.py --csv_input=images/train_labels.csv --image_dir=images/train --output_path=train.record``

``python generate_tfrecord.py --csv_input=images/test_labels.csv --image_dir=images/test --output_path=test.record``

3. Train



``python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/faster_rcnn_inception_v2_pets.config``

if python complains no package called net: do this at /tensorflow_models/models/research/slim

```export PYTHONPATH=/research:research/slim```

4. Export inference graph

``python export_inference_graph.py --input_type image_tensor --pipeline_config_path training/faster_rcnn_inception_v2_pets.config --trained_checkpoint_prefix training/model.ckpt-XXXX --output_directory inference_graph``