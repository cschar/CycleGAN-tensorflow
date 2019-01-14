

##seadoo2moto
#moto videos
#playlist https://www.youtube.com/watch?v=vIlWeQsUzyU&index=43&list=RDWnEXInpExFE

CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=seadoo2moto --phase=test --test_dir=./testseadoo2moto --which_direction=BtoA


<------- TRy adding this to a COPY of the data directory
https://www.youtube.com/watch?v=0T7C-Jl2FOk

seadoohorse2moto
==================

#train
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=seadoohorse2moto --sample_dir=sampleseadoo2moto



hockey2rugby
====================

#test
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=hockey2rugby --phase=test --test_dir=./h2rtest-80k-BtoA --which_direction=BtoA

#train
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=hockey2rugby --sample_dir=sampleh2r2

### 10x the learning rate
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=hockey2rugby --sample_dir=sampleh2r2 --lr=0.002



https://www.youtube.com/watch?v=4ikEjqDAdIg <-- long rugby video <alt training source>

 ####  jockey2moto

 https://www.youtube.com/watch?v=uAVok2bNDWs
 https://www.youtube.com/watch?v=-wKXihN1Z9E   <---- try first with moto data
 https://www.youtube.com/watch?v=wN-t1-M4zQM


 #### tennis2volley

 https://www.youtube.com/watch?v=hqRtwEZoiF4
 https://www.youtube.com/watch?v=4bUxoUVKmb4

CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=tennis2volley --sample_dir=samplet2v


CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=tennis2volley --phase=test --test_dir=./t2vtest-39k-BtoA --which_direction=BtoA
