# Awesome Machine Vision

> A curated list of practical computer vision, machine vision, edge AI, object detection, datasets, annotation tools, deployment runtimes, and production resources.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![GitHub Sponsors](https://img.shields.io/badge/Sponsor-mmaxjr-db61a2?logo=githubsponsors&logoColor=white)](https://github.com/sponsors/mmaxjr)
[![Topics](https://img.shields.io/badge/topics-computer--vision%20%7C%20edge--ai%20%7C%20fire--detection-blue)](https://github.com/mmaxjr/awesome-machine-vision)

Machine vision is where cameras, models, sensors, infrastructure, and operations meet. This list focuses on tools that help people build real systems: fire and smoke monitoring, industrial inspection, agricultural vision, safety analytics, security cameras, traffic analytics, robotics, and edge AI deployments.

I maintain this list as part of my work with DevOps, infrastructure automation, monitoring, and production computer vision, including a real project for detecting smoke and fire on farms in Brazil.

## Contents

- [Learning Paths](#learning-paths)
- [Practical Selection Guide](#practical-selection-guide)
- [Core Libraries](#core-libraries)
- [Recent Developments](#recent-developments)
- [Object Detection](#object-detection)
- [Segmentation](#segmentation)
- [Tracking](#tracking)
- [OCR and Document Vision](#ocr-and-document-vision)
- [Pose, Face, and Human Analysis](#pose-face-and-human-analysis)
- [Fire and Smoke Detection](#fire-and-smoke-detection)
- [Agriculture, Environment, and Remote Monitoring](#agriculture-environment-and-remote-monitoring)
- [Industrial Machine Vision](#industrial-machine-vision)
- [Datasets](#datasets)
- [Annotation Tools](#annotation-tools)
- [Dataset Management and Data Quality](#dataset-management-and-data-quality)
- [Training Frameworks](#training-frameworks)
- [Experiment Tracking and MLOps](#experiment-tracking-and-mlops)
- [Model Evaluation](#model-evaluation)
- [Model Formats and Conversion](#model-formats-and-conversion)
- [Inference Runtimes](#inference-runtimes)
- [Edge AI Hardware](#edge-ai-hardware)
- [Video Analytics and Streaming](#video-analytics-and-streaming)
- [Deployment Patterns](#deployment-patterns)
- [Production Readiness Checklist](#production-readiness-checklist)
- [Monitoring Production Vision Systems](#monitoring-production-vision-systems)
- [Security, Privacy, and Responsible AI](#security-privacy-and-responsible-ai)
- [Useful Awesome Lists](#useful-awesome-lists)
- [Contributing](#contributing)

## Learning Paths

- [OpenCV University](https://opencv.org/university/) - Courses and articles for computer vision and OpenCV.
- [CS231n: Deep Learning for Computer Vision](https://cs231n.stanford.edu/) - Classic Stanford course for image classification, CNNs, detection, and visual recognition.
- [Deep Learning for Computer Vision, Michigan](https://web.eecs.umich.edu/~justincj/teaching/eecs498/WI2022/) - Practical lecture material for modern vision.
- [PyImageSearch](https://pyimagesearch.com/) - Tutorials covering OpenCV, object detection, OCR, and deployment.
- [LearnOpenCV](https://learnopencv.com/) - Practical OpenCV and deep learning computer vision tutorials.
- [Roboflow Blog](https://blog.roboflow.com/) - Applied guides for datasets, annotation, YOLO, deployment, and evaluation.
- [Ultralytics Docs](https://docs.ultralytics.com/) - YOLO training, prediction, export, tracking, and deployment docs.
- [OpenMMLab Docs](https://openmmlab.com/) - Documentation and projects for detection, segmentation, pose, tracking, and deployment.

## Practical Selection Guide

Use this quick map when choosing tools for a real project:

| Scenario | Start with | Add when needed |
| --- | --- | --- |
| Fast object detection prototype | Ultralytics YOLO, Roboflow, OpenCV | SAHI for small objects, FiftyOne for error analysis |
| Industrial inspection | OpenCV, HALCON, camera SDKs | calibration, controlled lighting, PLC or alert integration |
| Fire and smoke monitoring | fire/smoke datasets, YOLO, video pipelines | temporal smoothing, weather-aware thresholds, human review |
| Farm or rural camera deployment | RTSP, edge device, local queue | offline sync, camera health metrics, solar/power monitoring |
| Large dataset cleanup | CVAT, Label Studio, FiftyOne | Cleanlab, DVC, active learning workflows |
| Edge inference | ONNX Runtime, OpenVINO, TensorRT | model quantization, runtime benchmarks, watchdog monitoring |
| Production monitoring | Prometheus, Grafana, Zabbix | drift checks, false positive review, alert fatigue metrics |

Before moving from a notebook to production, validate:

- camera placement, lens condition, frame rate, and night/day behavior
- latency on the target hardware, not only on a development machine
- false positives and false negatives by scene, camera, and time of day
- recovery behavior after network, power, or RTSP stream failures
- model version, dataset version, thresholds, and alert rules

## Core Libraries

- [OpenCV](https://github.com/opencv/opencv) - The standard computer vision library for image processing, camera I/O, calibration, tracking, and classical CV.
- [scikit-image](https://github.com/scikit-image/scikit-image) - Image processing algorithms for Python.
- [Pillow](https://github.com/python-pillow/Pillow) - Python Imaging Library fork for basic image handling.
- [Kornia](https://github.com/kornia/kornia) - Differentiable computer vision library for PyTorch.
- [Albumentations](https://github.com/albumentations-team/albumentations) - Fast image augmentation library widely used for detection and segmentation.
- [imgaug](https://github.com/aleju/imgaug) - Image augmentation for machine learning experiments.
- [TorchVision](https://github.com/pytorch/vision) - PyTorch datasets, transforms, models, and vision utilities.
- [TensorFlow Image](https://www.tensorflow.org/api_docs/python/tf/image) - TensorFlow image operations.
- [JAX Image](https://jax.readthedocs.io/en/latest/_autosummary/jax.image.html) - Image utilities for JAX workflows.

## Recent Developments

Resources reviewed on 2026-10-07 for current model and deployment directions:

- [YOLO26 model documentation](https://docs.ultralytics.com/models/) - Current Ultralytics model family covering detection, segmentation, semantic segmentation, depth, classification, pose, and oriented bounding boxes, with export paths for edge deployment.
- [SAM 3](https://github.com/facebookresearch/sam3) - Promptable concept segmentation for images and video using text or visual examples. Check the repository license and access requirements before using it in a product.
- [RT-DETRv4](https://github.com/chengruchou/RT-DETRv4) - Real-time detection research direction using vision foundation models for distillation and improved detector performance.
- [D-FINE](https://github.com/Peterande/D-FINE) - Real-time DETR detector based on fine-grained distribution refinement, with an emphasis on localization quality without additional inference cost.
- [RF-DETR](https://github.com/roboflow/rf-detr) - Real-time transformer detector with training and deployment workflows for custom datasets. Review the model and weight licenses separately.
- [Open Edge Platform Geti](https://github.com/open-edge-platform/geti) - Local platform for creating, training, optimizing, and deploying computer vision models, including OpenVINO-based export and video pipelines.
- [GLEE](https://github.com/FoundationVision/GLEE) - General object foundation model for image and video tasks, including open-world detection, tracking, and segmentation.
- [Vision-Language Models for Edge Networks](https://arxiv.org/abs/2502.07855) - Survey of compression, quantization, distillation, hardware, privacy, and deployment constraints for VLMs at the edge.

When evaluating a new model, compare more than benchmark accuracy: measure latency on the target hardware, memory use, power draw, licensing, export stability, calibration, false-alert rate, and behavior under the actual camera conditions.

## Object Detection

- [Ultralytics YOLO](https://github.com/ultralytics/ultralytics) - Popular YOLO package for object detection, segmentation, pose, classification, tracking, and export.
- [YOLOv5](https://github.com/ultralytics/yolov5) - Widely used YOLO implementation with a large ecosystem.
- [YOLOX](https://github.com/Megvii-BaseDetection/YOLOX) - Anchor-free YOLO detector.
- [MMDetection](https://github.com/open-mmlab/mmdetection) - OpenMMLab object detection toolbox with many model families.
- [Detectron2](https://github.com/facebookresearch/detectron2) - Meta AI object detection and segmentation framework.
- [TensorFlow Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection) - TensorFlow model zoo and detection training pipeline.
- [PaddleDetection](https://github.com/PaddlePaddle/PaddleDetection) - Detection toolbox from PaddlePaddle.
- [RT-DETR](https://github.com/lyuwenyu/RT-DETR) - Real-time detection transformer.
- [D-FINE](https://github.com/Peterande/D-FINE) - Detection foundation model for real-time object detection.
- [DETR](https://github.com/facebookresearch/detr) - End-to-end object detection with transformers.
- [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) - Open-set object detection with language prompts.
- [OWLv2](https://huggingface.co/docs/transformers/model_doc/owlv2) - Open-vocabulary object detection model in Transformers.
- [SAHI](https://github.com/obss/sahi) - Slicing aided hyper inference for small object detection in large images.
- [Supervision](https://github.com/roboflow/supervision) - Reusable utilities for detections, annotations, tracking, zones, and counting.

## Segmentation

- [Segment Anything](https://github.com/facebookresearch/segment-anything) - Promptable image segmentation model.
- [Segment Anything 2](https://github.com/facebookresearch/sam2) - Segment Anything for images and videos.
- [MMSegmentation](https://github.com/open-mmlab/mmsegmentation) - OpenMMLab semantic segmentation toolbox.
- [Detectron2](https://github.com/facebookresearch/detectron2) - Instance segmentation and panoptic segmentation.
- [Segmentation Models PyTorch](https://github.com/qubvel-org/segmentation_models.pytorch) - PyTorch segmentation models with common encoders.
- [U-Net](https://arxiv.org/abs/1505.04597) - Foundational biomedical segmentation architecture.
- [Mask R-CNN](https://arxiv.org/abs/1703.06870) - Classic instance segmentation architecture.
- [YOLO segmentation](https://docs.ultralytics.com/tasks/segment/) - Instance segmentation using Ultralytics models.

## Tracking

- [ByteTrack](https://github.com/ifzhang/ByteTrack) - Multi-object tracking by associating almost every detection box.
- [BoT-SORT](https://github.com/NirAharon/BoT-SORT) - Robust multi-object tracker.
- [Deep SORT](https://github.com/nwojke/deep_sort) - Tracking-by-detection with deep appearance descriptors.
- [Norfair](https://github.com/tryolabs/norfair) - Lightweight Python multi-object tracking library.
- [MMTracking](https://github.com/open-mmlab/mmtracking) - OpenMMLab video perception and tracking toolbox.
- [OpenCV Tracking](https://docs.opencv.org/4.x/d9/df8/group__tracking.html) - Classical tracking algorithms in OpenCV.

## OCR and Document Vision

- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) - Open source OCR engine.
- [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR) - Multilingual OCR toolkit.
- [EasyOCR](https://github.com/JaidedAI/EasyOCR) - Ready-to-use OCR in Python.
- [docTR](https://github.com/mindee/doctr) - Document text detection and recognition.
- [TrOCR](https://huggingface.co/docs/transformers/model_doc/trocr) - Transformer OCR models.
- [LayoutParser](https://github.com/Layout-Parser/layout-parser) - Toolkit for document image analysis.
- [Donut](https://github.com/clovaai/donut) - OCR-free document understanding transformer.

## Pose, Face, and Human Analysis

- [MediaPipe](https://github.com/google-ai-edge/mediapipe) - Cross-platform perception pipelines for pose, hands, face, and more.
- [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose) - Real-time multi-person keypoint detection.
- [MMPose](https://github.com/open-mmlab/mmpose) - OpenMMLab pose estimation toolbox.
- [InsightFace](https://github.com/deepinsight/insightface) - 2D and 3D face analysis.
- [DeepFace](https://github.com/serengil/deepface) - Face recognition and facial attribute analysis.
- [face_recognition](https://github.com/ageitgey/face_recognition) - Simple face recognition API built on dlib.
- [YOLO pose](https://docs.ultralytics.com/tasks/pose/) - Pose estimation with Ultralytics models.

## Fire and Smoke Detection

Resources for wildfire detection, farm monitoring, environmental risk, cameras in rural areas, and early warning systems.

- [D-Fire Dataset](https://github.com/gaia-solutions-on-demand/DFireDataset) - Image dataset for fire and smoke object detection with more than 21,000 images.
- [FireNet](https://github.com/arpit-jadon/FireNet-LightWeight-Network-for-Fire-Detection) - Lightweight fire detection network.
- [YOLOv8 Fire and Smoke Detection](https://github.com/Abonia1/YOLOv8-Fire-and-Smoke-Detection) - Fire and smoke tracking and detection using YOLOv8.
- [Fire Detection topic on GitHub](https://github.com/topics/fire-detection) - Repositories tagged with fire detection.
- [Smoke Detection topic on GitHub](https://github.com/topics/smoke-detection) - Repositories tagged with smoke detection.
- [Forest Fire Detection topic on GitHub](https://github.com/topics/forest-fire-detection) - Repositories tagged with forest fire detection.
- [Wildfire Detection topic on GitHub](https://github.com/topics/wildfire-detection) - Repositories tagged with wildfire detection.
- [FIgLib and wildfire research datasets](https://github.com/DeepQuestAI/Fire-Smoke-Dataset) - Fire and smoke image resources.
- [HPWREN Cameras](https://hpwren.ucsd.edu/cameras/) - Public camera network used in wildfire research and monitoring.
- [AlertWildfire](https://www.alertwildfire.org/) - Wildfire camera network and situational awareness system.

Practical notes for fire and smoke systems:

- Use video clips, not only still images. Smoke evolves over time.
- Include negative samples: clouds, fog, dust, sunlight, soil, shadows, machinery, and camera glare.
- Separate `fire`, `smoke`, and `smoke-like` labels when possible.
- Track false positives by camera, time of day, weather, crop type, and lens condition.
- Add confidence thresholds by zone. A camera pointed at a road needs different thresholds from a camera pointed at dry pasture.
- Keep human review in the loop for alarms that trigger operational response.

## Agriculture, Environment, and Remote Monitoring

- [PlantCV](https://github.com/danforthcenter/plantcv) - Image analysis software for plant phenotyping.
- [AgML](https://github.com/Project-AgML/AgML) - Agricultural machine learning datasets and tools.
- [DeepForest](https://github.com/weecology/DeepForest) - Tree crown detection from aerial imagery.
- [TorchGeo](https://github.com/microsoft/torchgeo) - Geospatial datasets and models for PyTorch.
- [Raster Vision](https://github.com/azavea/raster-vision) - Framework for deep learning on satellite and aerial imagery.
- [GeoPandas](https://github.com/geopandas/geopandas) - Geospatial data analysis in Python.
- [QGIS](https://github.com/qgis/QGIS) - Open source geographic information system.
- [OpenDroneMap](https://github.com/OpenDroneMap/ODM) - Drone mapping and photogrammetry.
- [Sentinel Hub](https://www.sentinel-hub.com/) - Satellite imagery API and tooling.
- [NASA FIRMS](https://firms.modaps.eosdis.nasa.gov/) - Fire Information for Resource Management System.

## Industrial Machine Vision

- [HALCON](https://www.mvtec.com/products/halcon) - Commercial machine vision software for industrial inspection.
- [Cognex VisionPro](https://www.cognex.com/products/machine-vision/vision-software/visionpro-software) - Industrial vision software.
- [Basler pylon SDK](https://www.baslerweb.com/en/software/pylon/) - Camera SDK for Basler industrial cameras.
- [FLIR Spinnaker SDK](https://www.flir.com/products/spinnaker-sdk/) - Camera SDK for FLIR/Teledyne cameras.
- [GenICam](https://www.emva.org/standards-technology/genicam/) - Generic programming interface for machine vision cameras.
- [Aravis](https://github.com/AravisProject/aravis) - Vision library for GenICam cameras.
- [OpenPnP](https://github.com/openpnp/openpnp) - Open source SMT pick-and-place software with machine vision components.
- [OpenCV Calibration](https://docs.opencv.org/4.x/dc/dbb/tutorial_py_calibration.html) - Camera calibration basics.

## Datasets

- [COCO](https://cocodataset.org/) - Common Objects in Context dataset for detection, segmentation, and captioning.
- [Open Images](https://storage.googleapis.com/openimages/web/index.html) - Large-scale image dataset with labels, boxes, and segmentation masks.
- [ImageNet](https://www.image-net.org/) - Large-scale image classification dataset.
- [Visual Genome](https://homes.cs.washington.edu/~ranjay/visualgenome/) - Dense annotations for objects, attributes, and relationships.
- [KITTI](https://www.cvlibs.net/datasets/kitti/) - Autonomous driving vision benchmark.
- [Cityscapes](https://www.cityscapes-dataset.com/) - Urban scene understanding dataset.
- [BDD100K](https://www.bdd100k.com/) - Driving dataset with images, video, detection, lane, and segmentation labels.
- [Mapillary Vistas](https://www.mapillary.com/dataset/vistas) - Street-level semantic segmentation dataset.
- [Roboflow Universe](https://universe.roboflow.com/) - Public computer vision datasets across many domains.
- [Kaggle Datasets](https://www.kaggle.com/datasets) - Public datasets for image classification, detection, and segmentation.
- [Hugging Face Datasets](https://huggingface.co/datasets?modality=modality:image) - Image datasets hosted on Hugging Face.
- [Papers With Code Datasets](https://paperswithcode.com/datasets) - Dataset index connected to papers and benchmarks.

## Annotation Tools

- [CVAT](https://github.com/cvat-ai/cvat) - Open source annotation tool for images and videos.
- [Label Studio](https://github.com/HumanSignal/label-studio) - Multi-modal data labeling platform.
- [LabelImg](https://github.com/HumanSignal/labelImg) - Simple graphical image annotation tool.
- [Labelme](https://github.com/wkentaro/labelme) - Polygon annotation tool.
- [Roboflow Annotate](https://roboflow.com/annotate) - Hosted annotation and dataset workflow.
- [VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/) - Lightweight browser-based annotation tool.
- [makesense.ai](https://www.makesense.ai/) - Free online image annotation tool.
- [Supervisely](https://supervisely.com/) - Computer vision platform for annotation, training, and deployment.
- [Encord](https://encord.com/) - Data platform for annotation and model evaluation.
- [Dataloop](https://dataloop.ai/) - Data management and annotation platform.

## Dataset Management and Data Quality

- [FiftyOne](https://github.com/voxel51/fiftyone) - Dataset visualization, curation, evaluation, and error analysis.
- [Cleanlab](https://github.com/cleanlab/cleanlab) - Find label errors and improve dataset quality.
- [Lightly](https://github.com/lightly-ai/lightly) - Data curation and active learning for computer vision.
- [DVC](https://github.com/iterative/dvc) - Version control for data and ML pipelines.
- [LakeFS](https://github.com/treeverse/lakeFS) - Data lake version control.
- [Datumaro](https://github.com/open-edge-platform/datumaro) - Dataset management, conversion, and transformation.
- [FiftyOne Brain](https://docs.voxel51.com/user_guide/brain.html) - Similarity, uniqueness, and mistake analysis.
- [Roboflow](https://roboflow.com/) - Dataset hosting, conversion, augmentation, and deployment workflows.

## Training Frameworks

- [PyTorch](https://github.com/pytorch/pytorch) - Deep learning framework widely used in research and production.
- [TensorFlow](https://github.com/tensorflow/tensorflow) - Deep learning framework with training and deployment ecosystem.
- [Keras](https://github.com/keras-team/keras) - High-level deep learning API.
- [PyTorch Lightning](https://github.com/Lightning-AI/pytorch-lightning) - Structured PyTorch training.
- [Hugging Face Transformers](https://github.com/huggingface/transformers) - Vision transformers, multimodal models, and training utilities.
- [Hugging Face Accelerate](https://github.com/huggingface/accelerate) - Distributed and mixed-precision training.
- [OpenMMLab](https://github.com/open-mmlab) - Ecosystem for detection, segmentation, pose, tracking, and deployment.
- [Ultralytics](https://github.com/ultralytics/ultralytics) - End-to-end YOLO training, validation, prediction, export, and tracking.
- [timm](https://github.com/huggingface/pytorch-image-models) - Large collection of PyTorch image models.
- [NVIDIA TAO Toolkit](https://developer.nvidia.com/tao-toolkit) - Transfer learning toolkit for vision models.

## Experiment Tracking and MLOps

- [MLflow](https://github.com/mlflow/mlflow) - Experiment tracking, model registry, and deployment workflows.
- [Weights & Biases](https://wandb.ai/) - Experiment tracking and model monitoring.
- [ClearML](https://github.com/clearml/clearml) - Experiment management, orchestration, and data management.
- [DVC](https://github.com/iterative/dvc) - Data and pipeline versioning.
- [Kubeflow](https://github.com/kubeflow/kubeflow) - ML workflows on Kubernetes.
- [Metaflow](https://github.com/Netflix/metaflow) - Human-friendly ML workflows.
- [ZenML](https://github.com/zenml-io/zenml) - MLOps framework for pipelines.
- [BentoML](https://github.com/bentoml/BentoML) - Model serving framework.
- [Seldon Core](https://github.com/SeldonIO/seldon-core) - Model deployment on Kubernetes.
- [KServe](https://github.com/kserve/kserve) - Kubernetes model serving.

## Model Evaluation

- [COCO API](https://github.com/cocodataset/cocoapi) - Standard metrics for detection and segmentation.
- [TorchMetrics](https://github.com/Lightning-AI/torchmetrics) - Metrics for PyTorch and Lightning.
- [FiftyOne Evaluation](https://docs.voxel51.com/user_guide/evaluation.html) - Visual model evaluation and failure analysis.
- [Supervision Metrics](https://supervision.roboflow.com/) - Utilities for detections and analysis.
- [pycocotools](https://github.com/ppwwyyxx/cocoapi) - Maintained COCO API fork.
- [mean-average-precision](https://github.com/bes-dev/mean_average_precision) - mAP implementation for object detection.

Production evaluation checklist:

- Track false positives and false negatives separately.
- Evaluate by camera, scene, lighting, weather, and time of day.
- Save low-confidence and high-impact examples for review.
- Use a holdout set that reflects real deployment cameras.
- Measure latency, throughput, memory, and dropped frames, not only mAP.

## Model Formats and Conversion

- [ONNX](https://github.com/onnx/onnx) - Open Neural Network Exchange model format.
- [ONNX Runtime](https://github.com/microsoft/onnxruntime) - Cross-platform inference runtime for ONNX models.
- [TensorRT](https://developer.nvidia.com/tensorrt) - NVIDIA SDK for optimized deep learning inference.
- [OpenVINO](https://github.com/openvinotoolkit/openvino) - Intel toolkit for optimized model inference.
- [TensorFlow Lite](https://www.tensorflow.org/lite) - Lightweight inference for mobile and edge devices.
- [Core ML Tools](https://github.com/apple/coremltools) - Convert models for Apple platforms.
- [NCNN](https://github.com/Tencent/ncnn) - High-performance neural network inference framework for mobile.
- [MNN](https://github.com/alibaba/MNN) - Lightweight deep learning framework.
- [TVM](https://github.com/apache/tvm) - Deep learning compiler stack.
- [Open Neural Network Compiler](https://github.com/onnx/onnx-mlir) - ONNX-MLIR compiler.

## Inference Runtimes

- [Triton Inference Server](https://github.com/triton-inference-server/server) - NVIDIA inference server supporting multiple backends.
- [NVIDIA DeepStream](https://developer.nvidia.com/deepstream-sdk) - Streaming analytics SDK for video AI.
- [OpenVINO Runtime](https://docs.openvino.ai/) - Runtime for Intel CPUs, GPUs, VPUs, and edge hardware.
- [ONNX Runtime](https://onnxruntime.ai/) - ONNX inference across CPU, GPU, mobile, and edge.
- [TensorFlow Serving](https://github.com/tensorflow/serving) - Serving system for TensorFlow models.
- [TorchServe](https://github.com/pytorch/serve) - Serving PyTorch models.
- [OpenCV DNN](https://docs.opencv.org/4.x/d2/d58/tutorial_table_of_content_dnn.html) - Inference using OpenCV's DNN module.
- [NVIDIA Jetson Inference](https://github.com/dusty-nv/jetson-inference) - Deep learning inference and training demos for Jetson.

## Edge AI Hardware

- [NVIDIA Jetson](https://developer.nvidia.com/embedded-computing) - Edge AI platform for accelerated vision applications.
- [Raspberry Pi](https://www.raspberrypi.com/) - Low-cost single-board computers for camera and edge experiments.
- [Google Coral](https://coral.ai/) - Edge TPU hardware for efficient inference.
- [Intel Neural Compute Stick](https://www.intel.com/content/www/us/en/developer/tools/neural-compute-stick/overview.html) - USB VPU accelerator.
- [Luxonis OAK](https://github.com/luxonis/depthai) - DepthAI cameras with onboard AI.
- [Hailo](https://hailo.ai/) - AI accelerators for edge devices.
- [Sony Spresense](https://developer.sony.com/spresense/) - Low-power board for edge sensing.
- [ESP32-CAM](https://www.espressif.com/en/products/socs/esp32) - Low-cost microcontroller camera platform.
- [Seeed Studio reComputer](https://www.seeedstudio.com/reComputer-Jetson-c-2703.html) - Jetson-based edge AI systems.

## Video Analytics and Streaming

- [GStreamer](https://gstreamer.freedesktop.org/) - Multimedia framework for video pipelines.
- [FFmpeg](https://github.com/FFmpeg/FFmpeg) - Video processing, transcoding, and streaming.
- [MediaMTX](https://github.com/bluenviron/mediamtx) - RTSP, RTMP, WebRTC, and HLS media server.
- [Frigate](https://github.com/blakeblackshear/frigate) - NVR with real-time object detection.
- [ZoneMinder](https://github.com/ZoneMinder/zoneminder) - Open source video surveillance software.
- [Shinobi](https://gitlab.com/Shinobi-Systems/Shinobi) - CCTV and NVR platform.
- [WebRTC](https://webrtc.org/) - Real-time browser video transport.
- [RTSP](https://en.wikipedia.org/wiki/Real_Time_Streaming_Protocol) - Common IP camera streaming protocol.
- [SRS](https://github.com/ossrs/srs) - Simple Realtime Server for streaming.

## Deployment Patterns

- Camera to edge device to alerting API.
- RTSP camera to GStreamer or FFmpeg pipeline to inference runtime.
- Edge inference with local queue and cloud synchronization.
- Batch image processing for drone, satellite, or inspection imagery.
- Human-in-the-loop review dashboard for high-impact alerts.
- Model service behind REST or gRPC with async worker queues.
- Multi-camera deployment with per-camera thresholds and health checks.
- Kubernetes deployment for centralized inference.
- Offline-first deployment for rural areas with unstable connectivity.

Example fire/smoke production architecture:

```text
IP cameras / rural towers
        |
        v
RTSP ingest -> frame sampler -> detection model -> temporal smoothing
        |                              |
        |                              v
        |                       event confidence
        v                              |
camera health                    alert rules
        |                              |
        v                              v
monitoring dashboard       WhatsApp/SMS/email/radio workflow
        |
        v
logs, clips, false positive review, retraining dataset
```

## Production Readiness Checklist

Use this checklist before moving a machine vision pipeline from a demo to a
production camera or edge device:

- **Define the decision:** document the classes, confidence thresholds, alert
  cooldowns, and which cases require human confirmation.
- **Validate representative data:** test day/night, rain, fog, glare, camera
  movement, occlusion, seasonal changes, and the actual camera placement.
- **Measure the pipeline:** record end-to-end latency, throughput, dropped
  frames, reconnects, and resource usage rather than model accuracy alone.
- **Handle degraded operation:** define behavior for a disconnected camera,
  full disk, unavailable model service, stale frames, and loss of upstream
  connectivity.
- **Keep evidence traceable:** retain model, dataset, configuration, and
  deployment versions with each alert and review false positives and false
  negatives regularly.
- **Test alert delivery:** verify retries, deduplication, escalation, and a
  clear recovery path before relying on the system for safety decisions.
- **Plan updates and rollback:** stage model or threshold changes, compare
  them against a fixed evaluation set, and keep the previous deployment ready
  to restore.

## Monitoring Production Vision Systems

- [Prometheus](https://github.com/prometheus/prometheus) - Metrics collection and alerting.
- [Grafana](https://github.com/grafana/grafana) - Dashboards and observability.
- [Zabbix](https://www.zabbix.com/) - Infrastructure and service monitoring.
- [OpenTelemetry](https://opentelemetry.io/) - Observability standard for traces, metrics, and logs.
- [Loki](https://github.com/grafana/loki) - Log aggregation.
- [Sentry](https://github.com/getsentry/sentry) - Error tracking.
- [Evidently AI](https://github.com/evidentlyai/evidently) - ML monitoring and data drift checks.
- [WhyLabs](https://whylabs.ai/) - ML observability platform.

Useful metrics:

- Camera online/offline state.
- Frames per second received.
- Frames per second processed.
- Inference latency p50, p95, p99.
- Model confidence distribution.
- Alert count by camera and class.
- False positive and false negative review counts.
- Dropped frames and reconnect attempts.
- Disk usage for video clips.
- Temperature, CPU, GPU, RAM, and power status on edge devices.

## Security, Privacy, and Responsible AI

- [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) - Security risks for ML systems.
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) - AI risk management guidance.
- [Model Cards](https://modelcards.withgoogle.com/about) - Documentation approach for model behavior and limits.
- [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) - Dataset documentation practice.
- [Adversarial Robustness Toolbox](https://github.com/Trusted-AI/adversarial-robustness-toolbox) - Tools for adversarial ML robustness.
- [Privacy Badger](https://privacybadger.org/) - Useful reference for privacy-aware systems.

Responsible deployment checklist:

- Document what the model can and cannot detect.
- Keep humans in the loop for safety-critical decisions.
- Store only the video clips needed for verification and improvement.
- Avoid face/person identification unless it is required and legally approved.
- Record model versions, dataset versions, and alert rules.
- Test under local weather, lighting, camera angle, and connectivity conditions.

## Useful Awesome Lists

- [awesome-computer-vision](https://github.com/jbhuang0604/awesome-computer-vision) - Broad computer vision resource list.
- [awesome-deep-vision](https://github.com/kjw0612/awesome-deep-vision) - Deep learning for computer vision resources.
- [awesome-object-detection](https://github.com/amusi/awesome-object-detection) - Object detection papers and resources.
- [awesome-semantic-segmentation](https://github.com/mrgloom/awesome-semantic-segmentation) - Semantic segmentation resources.
- [awesome-visual-transformer](https://github.com/dk-liang/Awesome-Visual-Transformer) - Vision transformer resources.
- [awesome-edge-ai](https://github.com/ashishpatel26/awesome-edge-ai) - Edge AI resources.
- [awesome-mlops](https://github.com/visenger/awesome-mlops) - MLOps resources.
- [awesome-production-machine-learning](https://github.com/EthicalML/awesome-production-machine-learning) - Production ML resources.
- [awesome-opencv](https://github.com/sshkhr/awesome-opencv) - OpenCV resources.

## Contributing

Contributions are welcome. Good additions should be useful for people building real computer vision or machine vision systems.

Before adding a link, check:

- Is the project active or still useful?
- Does it solve a real computer vision problem?
- Is the description clear and neutral?
- Is it open source, documented, or widely used?
- Would it help someone building, deploying, monitoring, or maintaining a vision system?

Suggested format:

```markdown
- [Project Name](https://example.com) - One short sentence explaining why it matters.
```

## Maintainer

Maintained by [Marcos Max](https://github.com/mmaxjr), DevOps and infrastructure engineer working with automation, monitoring, networking, Python, and production computer vision for smoke and fire detection in Brazilian farms.

If this list helps your work, consider supporting it through [GitHub Sponsors](https://github.com/sponsors/mmaxjr).
