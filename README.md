<!--<!DOCTYPE html>-->
<!-- saved from url=(0014)about:internet -->
<html lang=" en-US"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>NLP Class Project | Spring 2025 CSCI 5541 | University of Minnesota</title>

  <link rel="stylesheet" href="./files/bulma.min.css" />

  <link rel="stylesheet" href="./files/styles.css">
  <link rel="preconnect" href="https://fonts.gstatic.com/">
  <link href="./files/css2" rel="stylesheet">
  <link href="./files/css" rel="stylesheet">


  <base href="." target="_blank"></head>


<body>
  <div>
    <div class="wrapper">
      <h1 style="font-family: &#39;Lato&#39;, sans-serif;">Speech-to-Text: Translate Dialects to Official Vietnamese Language</h1>
      <h4 style="font-family: &#39;Lato&#39;, sans-serif; ">Spring CSCI 5541 NLP: Class Project - University of Minnesota</h4>
      <h4 style="font-family: &#39;Lato&#39;, sans-serif; ">The Parsing Pals</h4>

      <div class="authors-wrapper">
        
        <div class="author-container">
          <div class="author-image">
                        
              <img src="">
            
            
          </div>
          <p>
                        
              Member 1: Bang Ly
            
          </p>
        </div>
        
        <div class="author-container">
          <div class="author-image">
            
            <img src="">
            
          </div>
          <p>
            
            Member 2: Khanh Chi Le
            
          </p>
        </div>
        
        <div class="author-container">
          <div class="author-image">
            
              <img src="">            
            
          </div>
          <p>
              Member 3: Huong Giang To
          </p>
        </div>
        
<!--         <div class="author-container">
          <div class="author-image">
                        
              <img src="">
            
          </div>
          <p>
            Member 4
          </p>
        </div> -->
        
      </div>

      <br/>

      <div class="authors-wrapper">
        <div class="publication-links">
          <!-- Github link -->
          <span class="link-block">
            <a
              href=""
              target="_blank"
              class="external-link button is-normal is-rounded is-dark is-outlined"
            >
            <span>Final Report</span>
            </a>
          </span>
          <span class="link-block">
            <a
              href=""
              target="_blank"
              class="external-link button is-normal is-rounded is-dark is-outlined"
            >
            <span>Code</span>
            </a>
          </span>      
          <span class="link-block">
            <a
              href=""
              target="_blank"
              class="external-link button is-normal is-rounded is-dark is-outlined"
            >
            <span>Model Weights</span>
            </a>
          </span>              
        </div>
      </div>


    </div>
  </div>





  
  


  <div class="wrapper">
    <hr>
    
    <h2 id="abstract">Abstract</h2>

<p>
  Vietnamese exhibits diverse phonetic variations, which pose significant challenges for state-of-the-art speech-to-text systems. 
  While progress in Vietnamese speech-to-text technology has been substantial, with advancements in pre-trained models and speech recognition systems, 
  their performance in handling multiple dialects remains poor. To address this, we aim to fine-tune existing models to improve their ability to translate various dialects more effectively. 
  Building on this, we hope to develop a system where the model processes dialectal speech and, instead of providing a direct word-for-word transcription, generates standard Vietnamese text 
  -  bridging communication gaps within the community.
</p>

<hr>

<h2 id="teaser">Teaser Figure</h2>

<p>A figure that conveys the main idea behind the project or the main application being addressed. This figure is from</p>

<p class="sys-img"><img src="./csci5541_webtemplate/files/teaser.png" alt="imgname"></p>


<h3 id="the-timeline-and-the-highlights">Any subsection</h3>

<p>If you need to explain more about your figure</p>

<hr>

<h2 id="introduction">Introduction / Background / Motivation</h2>

<p>
 
Recently, the speech recognition community has made significant progress in building Deep Neural Networks (DNNs) for Speech-to-Text (STT) or
Speech-to-Text Recognition (STR) by utilizing vast amounts of training data and high-quality test sets.
Studies have shown that while current STT models perform well for high-resource languages
like French, English, and Mandarin, low-resource languages experience higher Word Error Rates
(WER) due to limited data. This challenge is even more pronounced in languages with diverse
phonetic variations and multiple dialects, such as Vietnamese (Ahlawat et al., 2025). 
</p>
<p>
Dialectal regions in Vietnam can have significantly different vocabularies, pronunciations, and tones, creating language
barriers even among Vietnamese speakers from different provinces. With recent advancements in Vietnamese NLP and Speech-to-Text systems, we aim to build
an STT pipeline that processes dialectal speech and, instead of providing a direct word-for-word transcription, generates standardized Vietnamese text.
</p>

<hr>

<h2 id="approach">Approach</h2>

<p>
<b>What did you do exactly? How did you solve the problem? Why did you think it would be successful? Is anything new in your approach?</b>
</p>

<p>
Based on our pipeline, we take in input as audio files from the dataset: <a href="https://huggingface.co/datasets/nguyendv02/ViMD_Dataset">Multi-Dialect Vietnamese</a>, which is composed of 102.56 hours of data, representing 63 dialects in Vietnam. 
Due to the time limit in this course, we have chosen 4/5 dialects that has representative characterics for major dialects. The 4 dialects we chose are: 
<ul>
  <li>Hanoi (representative of Northern provinces)</li>
  <li>Saigon (representative of Southern provinces)</li>
  <li>Hue (representative of Central provinces)</li>
  <li>Nghe An (representative of dialects that contain heavy accents and unique local vocabulary) </li> 
</ul>
</p>
<p>
Using this audio input, we used PhoWhisper to generate the Vietnamese transcripts, and then we will fine tune PhoBERT to
generate the standardized translation to the dialectal transcripts.
</p>
<p>
We also collect audio data of dense dialectal voices from Youtube, Tiktok to add to our dataset. We will have to annotate these audio with standard language to get a reference text to compare with the PhoBert output. We expect to obtain 45 minutes - 1 hour worth of audio for each dialect.
</p>
<p>
We believe this is a reliable framework because of our strategy in choosing dialects, which is representative of all different common dialects in Vietnamese language.
Besides, the PhoWhisper and PhoBERT are model already fine tuned models in Vietnamese language. Our study will also include a comparative analysis on other LLMs such as 
GPT-3 and Qwen-3. (add why choose specifically gpt-3 and qwen-3)
</p>
<p>
The novelty in our work is the effort to deeply investigate the process of using LLMs to translate dialectal text to standardize text instead of just training LLMs based on multiple and diverse text (standardized text and dialectal text altogether)
and advance Vietnamese Speech-to-Text models from transcription to standardize-language-translation. 

</p>

<p>
<b>What problems did you anticipate? What problems did you encounter? Did the very first thing you tried work?</b>
</p>

<p>
<ol>
  <li>We are not sure which dialect we should chose as the fifth one </li>
  <li>The audio in the datasets that we currently use don't include many local vocabulary, which is an essential part of a dialect. Because of this, the result of the PhoWhisper is very close to the text transcription already, making our work of translating dialect to standard language not obvious.</li>
</ol>
</p>

<hr>
    
<h2 id="results">Results</h2>
<p>
<b>How did you measure success? What experiments were used? What were the results, both quantitative and qualitative? Did you succeed? Did you fail? Why?</b>
</p>
<p>
  Since we have only generated the transcripts of audio using PhoWhisper, we depend on the WER metric to measure how accurate the transcripts are compared to the text reference. 
</p>
<table>
  <thead>
    <tr>
      <th style="text-align: center"><strong>Dialect</strong></th>
      <th style="text-align: center">Nghe An</th>
      <th style="text-align: center">Hue</th>
      <th style="text-align: center">Ha Noi</th>
      <th style="text-align: center">Sai Gon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center"><strong>WER</strong></td>
      <td style="text-align: center">0.1285</td>
      <td style="text-align: center">0.1567</td>
      <td style="text-align: center">0.1141</td>
      <td style="text-align: center">0.1105</td>
    </tr>
  </tbody>
  <caption>Table 1. WER for the PhoWhisper's transcription</caption>
</table>
<!-- <br>
<div style="text-align: center;">
<img style="height: 300px;" alt="" src="./files/results.png">
</div>
<br><br> -->

<hr>



<h2 id="conclusion">Conclustion and Future Work</h2>
<p>

  How easily are your results able to be reproduced by others?
  Did your dataset or annotation affect other people's choice of research or development projects to undertake?
  Does your work have potential harm or risk to our society? What kinds? If so, how can you address them?
  What limitations does your model have? How can you extend your work for future research?</p>

<p>
  - Our results might be easily reproduced by others since the pipeline is relatively simple. However, since there is not much data 
  on dialectal Vietnamese language systematically collected and annotated even though these dialects are still used prominently in each region, 
  combined with the fact that the PhoWhisper and PhoBERT model are new, no work has been done on this yet.
</p>
<p>
  - Some limitations our model might have is its runtime. It took us 50 mins to load the dataset, and 1.5 hours to run the PhoWhisper model on 
  4 different dialects. 

</p>
<hr>


  </div>
  


</body></html>
