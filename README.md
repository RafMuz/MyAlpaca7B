# About
Details about the Alpaca 7B model I made: 

You can check out the Model at [HuggingFace](https://huggingface.co/RafMuz/alpaca7B-lora/blob/main/README.md)  
This Model was created as a study experiment, to re-create alpaca on my end.  

# How it was made
Here I'll go into how I Fine-tuned & Quantized the model: 

## Fine Tuning
For this, I did need to pay for Google Colab credits so that I could use an A100. It took about 50 credits ($5) to Fine-tune it.  
If you want to do it for free, then you could try to do it with Kaggle's notebooks and it's 2xT4 ( *Google Colab only gives you 1xT4 in it's free teir* ), but I couldn't get it to work ( *too many problems with setting up the enviorment* ).  

Nonetheless if you want to use Kaggle then here's my notebook, as it might be useful to you: [Fine-tuning Weights on <ins>Kaggle Notebook</ins>](https://www.kaggle.com/code/rafmuz/finetune-llama/notebook)  
And here's the notebook for Google Colab: [Fine-tuning Weights on <ins>Google Colab</ins>](https://colab.research.google.com/drive/1MniDw2Ln4bGACokkqo4mZP071AFjDjz0#scrollTo=hPtf750brYSg)

A video on Fine-tuning LLaMA to make Alpaca in Google Colab: [Video on Fine-tuning Weights in Google Colab](https://youtu.be/LSoqyynKU9E) 

### Merge Weights

Once it's Fine-tuned, then I merged the finetuned weights file *(adapter_model.bin)*, with the base model. This was done because it's needed for quantization with llama.cpp, as far as I know. You can check the code out here:  
  Google Colab: [Merge Weights code on <ins>Colab</ins>](https://colab.research.google.com/drive/1A_owNNK5YRANuHMtFOtl9EiyQurYAqYd?usp=sharing)  
  Kaggle Notebook: [Merge Weights code on <ins>Kaggle</ins>](https://www.kaggle.com/code/rafmuz/merge-weights/notebook)  

## Quantization
For Quantization, I did 4-bit quantization with both [GPT-Q](https://github.com/qwopqwop200/GPTQ-for-LLaMa) and [llama.cpp](https://github.com/ggerganov/llama.cpp).  
With running both models, I found llama.cpp to be better in both training time & final output than GPT-Q, with the tradeoff of filesize.

I used Google Colab for this, as I found that Kaggle has problems with it's python enviorment for this stuff. You can check it out here:  
  Google Colab Notebook: [Quantize Model with GPT-Q & llama.cpp on <ins>Google Colab</ins>](https://colab.research.google.com/drive/1OmFbWP_g4fjmzy45SzJBN22QpVyiLBWc?usp=sharing)

# 
 
And that's the end of the Readme, thanks for reading!
