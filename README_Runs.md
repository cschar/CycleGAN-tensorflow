

##seadoo2moto
#moto videos
#playlist https://www.youtube.com/watch?v=vIlWeQsUzyU&index=43&list=RDWnEXInpExFE

CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=seadoo2moto --phase=test --test_dir=./mototest3 --which_direction=BtoA


<------- TRy adding this to a COPY of the data directory
https://www.youtube.com/watch?v=0T7C-Jl2FOk

seadoohorse2moto

##if pasting is weird, open new terminal with default wraparound
ffmpeg -ss 01:10 -i $(youtube-dl -f 22 -g 'https://www.youtube.com/watch?v=_AArltTNRaA') -t 0:30 -f image2 boatout%06d.jpg


### hockey2rugby
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=hockey2rugby --phase=test --test_dir=./h2rtest1 --which_direction=BtoA

CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=hockey2rugby --sample_dir=sampleh2r2

 CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=seadoo2moto --sample_dir=sampleseadoo2moto




 ####  jockey2moto

 https://www.youtube.com/watch?v=uAVok2bNDWs
 https://www.youtube.com/watch?v=-wKXihN1Z9E   <---- try first with moto data
 https://www.youtube.com/watch?v=wN-t1-M4zQM