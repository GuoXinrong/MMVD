
## Dataset process

you can download MSR_data_cleaned.csv and Joern by running `get_data.sh`

### Step 1: clean Code 

run `scripts/process_dataset.py` to clean dataset and remove abnormal functions, which also get the glove, word2vec and other models that will be used to initialize node embedding by the graph model

### Step 2: Graph Extraction: Generate CPGs with the help of joern

run `scripts/processJoern.py` to extract .c file and run Joern to get corresponding edges.json and nodes.json

### Step 3: Image Generation

run `scripts/getImages.py` to check data after Joern and resample the data to produce [an balanced dataset](https://drive.google.com/file/d/1biGbJ4t3zxdYLw9-o_mPph8t_xVbW4RA/view?usp=sharing), and then generate images(i.e.,CPG)

## Baselines 

### UniXcoder

```shell
cd models/cunixcoder

# train UniXcoder modle
chmod u+x run.sh
sh run.sh

# save best-f1 UniXcoder code embeddings(function-level)
CUDA_VISIBLE_DEVICES=$CUDA python3 main.py --save_unixcoder_embedding

```

### Devign

```shell
cd models/devign
python main.py
```

### Ivdetect

```shell
cd models/ivdetect
python main.py
```

### Reveal

```shell
cd models/reveal/ggnn
python main.py --save_after_ggnn
cd ..
python main.py
```

 