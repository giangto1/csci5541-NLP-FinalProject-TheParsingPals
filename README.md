<!--<!DOCTYPE html>-->
<!-- saved from url=(0014)about:internet -->
<html lang=" en-US"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
  
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>NLP Class Project | Spring 2025 CSCI 5541 | University of Minnesota</title>

  <link rel="stylesheet" href="./csci5541_webtemplate/files/bulma.min.css" />

  <link rel="stylesheet" href="./csci5541_webtemplate/files/styles.css">
  <link rel="preconnect" href="https://fonts.gstatic.com/">
  <link href="./files/css2" rel="stylesheet">
  <link href="./files/css" rel="stylesheet">


  <base href="." target="_blank"></head>


<body>
  <div>
    <div class="wrapper">
      <h1 style="font-family: &#39;Lato&#39;, sans-serif;">Speech-to-Text: Translate Dialects to Official Vietnamese Language</h1>
      <h4 style="font-family: &#39;Lato&#39;, sans-serif; ">Spring 2025 CSCI 5541 NLP: Class Project - University of Minnesota</h4>
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
  Vietnamese exhibits diverse phonetic variations across regions, posing significant challenges for state-of-the-art speech-to-text (STT) systems. While recent advances in
pre-trained models have improved Vietnamese STT overall, their performance on dialectal speech remains limited. To address this issue, our project focuses on developing a pipeline that transcribes dialectal Vietnamese speech into standardized Vietnamese text – instead of providing a direct word-for-word transcription, the system generates standard Vietnamese to help bridge communication gaps within the community. Our work demonstrates the feasibility of this approach, showing that fine-tuning existing models on curated dialectal speech data can significantly improve performance in dialectal STT. In addition, we propose future directions for advancing Vietnamese STT, including more robust model adaptation and dialect-aware dataset development.
</p>

<hr>

<h2 id="teaser">Project Pipeline</h2>

<p>A figure that conveys the main idea behind the project or the main application being addressed.</p>

<p class="sys-img"><img src="./csci5541_webtemplate/files/pipeline.png" alt="imgname"></p>


<!-- <h3 id="the-timeline-and-the-highlights">Any subsection</h3>

<p>If you need to explain more about your figure</p> -->

<hr>

<h2 id="introduction">Introduction / Background / Motivation</h2>

<p>
Recently, the speech recognition community has made significant progress in building Deep Neural Networks (DNNs) for Speech-to-Text (STT) or Speech-to-Text Recognition (STR) by utilizing vast amounts of training data and high-quality test sets. Studies have shown that while current STT models perform well for high-resource languages like French, English, and Mandarin, low-resource languages experience higher Word Error Rates (WER) due to limited data. This challenge is even more pronounced in languages with diverse phonetic variations and multiple dialects, such as Vietnamese (Ahlawat et al., 2025).
</p>
<p>
Dialectal regions in Vietnam can have significantly different vocabularies, pronunciations, and tones, creating language barriers even among Vietnamese speakers from different provinces. With recent advancements in Vietnamese NLP and Speech-to-Text systems, we aim to build an STT pipeline that processes dialectal speech and, instead of providing a direct word-for-word transcription, generates standardized Vietnamese text.
</p>

<hr>

<h2 id="approach">Approach</h2>

<p>
<b>Dataset</b>
</p>

<p>
Based on our pipeline, we take in input as audio files from the dataset: <a href="https://huggingface.co/datasets/nguyendv02/ViMD_Dataset">Multi-Dialect Vietnamese</a>, which is composed of 102.56 hours of data, representing 63 dialects in Vietnam. The dataset also contains reference text, which we will use as labels to compare with the LLMs' outputs.  Due to the time limit in this course, we have chosen 4 dialects that has representative characterics for major dialects. The 4 dialects we chose are: 
<ul>
  <li>Level 1 (Easy) Standard Vietnamese, to verify model performance in a non-dialectal setting. The specific dialect used for this Ha Noi dialect.</li>
  <li>Level 2 (Medium - Lexical) Huế dialect (Central Vietnam), selected for its distinct vocabulary.</li>
  <li>Level 3 (Medium - Tonal) Hồ Chí Minh City dialect (Southern Vietnam), chosen for its tonal shifts.</li>
  <li>Level 4 (Hard) Nghệ An/Hà Tĩnh dialect, widely regarded as the most difficult due to heavy tone merging and extensive vocabulary divergence from the standard. </li> 
</ul>
</p>

<b>Pipeline</b>
<p> Using audio inputs, we first generate Vietnamese transcripts with the pre-trained PhoWhisper model. Based on its initial performance in terms of Word Error Rate (WER) and BERTScore, we fine-tune PhoWhisper to improve upon these baseline results. We then use PhoGPT to convert the dialectal transcripts into standardized Vietnamese. For benchmarking purposes, we also evaluate a parallel pipeline using OpenAI’s Whisper-large for automatic speech recognition (ASR) and GPT-4 for text normalization—two of the most advanced models in global speech and language processing. </p> 
<p> We consider this a reliable framework due to our deliberate selection of dialects that represent the most commonly spoken regional variations in Vietnamese. Additionally, both PhoWhisper and PhoGPT are models specifically fine-tuned for the Vietnamese language, making them well-suited for this task. Our study also includes a comparative analysis against OpenAI’s Whisper-large and GPT-4 to assess the effectiveness of language-specific versus general-purpose models. </p> 
<p> The novelty of our work lies in its in-depth exploration of how to leverage large language models (LLMs) to translate dialectal text into standardized Vietnamese, rather than simply training on a mixture of dialectal and standard inputs. This approach enhances Vietnamese STT systems by moving beyond basic transcription, enabling accurate and semantically coherent translation across dialects, and ultimately improving accessibility and communication for Vietnamese speakers worldwide. </p>

<hr>
<b></b>
    
<h2 id="results">Results</h2>
<p>
<b>PhoWhisper-large-1.55B pretrained model</b>
</p>
<p>
  To evaluate the output text, we depend on the WER and BERTScore metric to measure how accurate the transcripts are compared to the reference text. 
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
    <tr>
      <td style="text-align: center"><strong>BERT</strong></td>
      <td style="text-align: center">0.9124</td>
      <td style="text-align: center">0.9057</td>
      <td style="text-align: center">0.9176</td>
      <td style="text-align: center">0.9215</td>
    </tr>
  </tbody>
  <caption>Table 1. WER for the PhoWhisper's transcription</caption>
</table>


<p>Below are the WERs for each data point in each dialect
<br>
<img src='./csci5541_webtemplate/files/hanoi.png' alt='Hanoi WER'>
</br>
<br>
<img src='./csci5541_webtemplate/files/hue.png' alt='Hue WER'>
</br>
<br>
<img src='./csci5541_webtemplate/files/nghean.png' alt='Nghe An WER'>
</br>
<br>
<img src='./csci5541_webtemplate/files/saigon.png' alt='Sai Gon WER'>
</br>
</p>
<!-- <br>
<div style="text-align: center;">
<img style="height: 300px;" alt="" src="./files/results.png">
</div>
<br><br> -->
<b>PhoWhisper-large-1.55B finetuned model</b>
Initially, we performed finetuning for the model with 830 audio samples as the train set, 104 audio samples for the validation set, 104 audio samples for the test set. The following WER and BERT Score is obtained
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
      <td style="text-align: center">0.4424</td>
      <td style="text-align: center">0.2134</td>
      <td style="text-align: center">0.5785</td>
      <td style="text-align: center">0.3522</td>
    </tr>
    <tr>
      <td style="text-align: center"><strong>BERTScore</strong></td>
      <td style="text-align: center">0.8543</td>
      <td style="text-align: center">0.9088</td>
      <td style="text-align: center">0.8505</td>
      <td style="text-align: center">0.8797</td>
    </tr>
</tbody>
  <caption>Table 2. WER and BERTScore for the finetuned PhoWhisper's transcription</caption>
</table>

Since the output of the finetuned model is significantly worse compared to the baseline model, we exhaustively fine-tuned the model by varying the parameters: optimizer, learning rate, batch size, and train-validation-test split. We use the following parameter combinations and report the WER and BERTScore below:

<table border="1" style="border-collapse: collapse; text-align: center;">
  <caption><strong>WER and BERTScore under different training configurations</strong></caption>
  <thead>
    <tr>
      <th>Split</th>
      <th>Batch</th>
      <th>Optimizer</th>
      <th>LR</th>
      <th>WER</th>
      <th>BERT</th>
    </tr>
  </thead>
  <tbody>
    <!-- 80-10-10 split -->
    <tr><td rowspan="12">80-10-10</td><td rowspan="6">3</td><td>AdamW</td><td>1e-5</td><td>0.1521</td><td>0.9389</td></tr>
    <tr><td>AdamW</td><td>1e-6</td><td>0.2442</td><td>0.9117</td></tr>
    <tr><td>Adam</td><td>1e-5</td><td>0.1515</td><td>0.9425</td></tr>
    <tr><td>Adam</td><td>1e-6</td><td>0.2753</td><td>0.9043</td></tr>
    <tr><td>SGD</td><td>1e-5</td><td>0.2165</td><td>0.9155</td></tr>
    <tr><td>SGD</td><td>1e-6</td><td>0.2188</td><td>0.9147</td></tr>

    <tr><td rowspan="6">12</td><td>AdamW</td><td>1e-5</td><td>0.1522</td><td>0.9366</td></tr>
    <tr><td>AdamW</td><td>1e-6</td><td>0.2176</td><td>0.9206</td></tr>
    <tr><td>Adam</td><td>1e-5</td><td>0.1458</td><td>0.9382</td></tr>
    <tr><td>Adam</td><td>1e-6</td><td>0.2165</td><td>0.9200</td></tr>
    <tr><td>SGD</td><td>1e-5</td><td>0.2182</td><td>0.9147</td></tr>
    <tr><td>SGD</td><td>1e-6</td><td>0.2188</td><td>0.9147</td></tr>

    <!-- 90-5-5 split -->
    <tr><td rowspan="12">90-5-5</td><td rowspan="6">3</td><td>AdamW</td><td>1e-5</td><td>0.1755</td><td>0.9350</td></tr>
    <tr><td>AdamW</td><td>1e-6</td><td>0.2194</td><td>0.9202</td></tr>
    <tr><td>Adam</td><td>1e-5</td><td>0.1665</td><td>0.9361</td></tr>
    <tr><td>Adam</td><td>1e-6</td><td>0.2194</td><td>0.9233</td></tr>
    <tr><td>SGD</td><td>1e-5</td><td>0.2452</td><td>0.9129</td></tr>
    <tr><td>SGD</td><td>1e-6</td><td>0.2452</td><td>0.9122</td></tr>

    <tr><td rowspan="6">12</td><td>AdamW</td><td>1e-5</td><td>0.1716</td><td>0.9368</td></tr>
    <tr><td>AdamW</td><td>1e-6</td><td>0.2194</td><td>0.9226</td></tr>
    <tr><td>Adam</td><td>1e-5</td><td>0.1729</td><td>0.9354</td></tr>
    <tr><td>Adam</td><td>1e-6</td><td>0.2245</td><td>0.9212</td></tr>
    <tr><td>SGD</td><td>1e-5</td><td>0.2452</td><td>0.9122</td></tr>
    <tr><td>SGD</td><td>1e-6</td><td>0.2465</td><td>0.9121</td></tr>
  </tbody>
</table>

<p><b>Error Analysis</b></p>
<p>
  
  Since Nghe An is the hardest dialects, we expect the WER to be highest among these samples. Here are TOP 5 samples that have the highest WER from the Nghe An audio samples:
  <br>
  WER: 0.6000 <br>
  REF: cảm thấy tự tin hơn <br>
  HYP: <b>ờ</b> cảm thấy <b>a</b> tự tin hơn <b>hơn</b> <br>
  <b>Error type: added random words</b> <br>
  <br>
  WER: 0.5833<br>
  REF: thấy an tâm thôi cứ tốt sức khỏe cho cộng đồng thôi <br>
  HYP: thấy an tâm thôi <b>thôi</b> <b>tôi thắp</b> cho sức khoẻ <b>ổn đồng</b> thôi <br>
  <b>Error type: duplicate words, spelling, grammar, word order</b> <br>
  <br>
  WER: 0.4167 <br>
  REF: hôm nay tôi rất là vinh dự được khám của các ba bác sĩ chữa để mà tư vấn về sức khỏe nhất là xương khớp nghe tôi mừng quá chỉ dẫn rất là nhiệt tình <br>
  HYP: <b>sẽ ra bữa</b> hôm nay tôi rất vinh dự được ra khám của các bác sĩ chữa để mà tư vấn về sức khoẻ nhất nhất là cái là <b>sương</b> khớp nghe tôi mừng quá vì nó <b>chỉ</b> chỉ dẫn rất nhiệt tình <br>
  <b>Error type: spelling, added random words, duplicate words, missing words</b> <br>
  <br>
  WER: 0.3111 <br>
  REF: ủy ban nhân dân phường với coi như là đảng ủy phường kêu gọi thì tất cả những bác sĩ chúng tôi đều đăng ký hết tôi là người cao tuổi nhất coi như là cũng là người coi như là xung phong   tham gia <br>
  HYP: ủy ban nhân dân phường mới lại coi như đã đồng ý phường kêu gọi thì tất cả những bác sĩ là chúng tôi đều đăng ký hết tôi là <b>cái người</b> mà cao tuổi nhất là cũng là coi như là <b>cái người</b> mà coi như là xung phong tham gia <br>
  <b>Error type: duplicate words </b> <br>
  <br>
  WER: 0.3103 <br>
  REF: em cũng muốn là được sử dụng cái kỳ thi đánh giá năng lực này giống như là một cái con đường khác được xét tuyển vào đại học <br>
  HYP: em cũng muốn là được ờ sử dụng cái <b>kỳ thị giáng lực </b> này giống như một cái con đường khác ờ được <b>xét tiểu</b> đại học <br>
  <b>Error type: spelling, contain filler words</b> <br>

</p>
<hr>



<h2 id="conclusion">Conclusion and Future Work</h2>
<p><b>Conclusion</b></p>
<p>
  From the above figures and table, our conclusion is that the WER for all data points are low, which means the PhoWhisper model is making accurate transcripts. However, this is not what we are expecting. We expect too see words that are written wrongly in tonal and words that are unique to a local dialect, not a perfect spelling and perfect standardized language in the transcripts, especially for hard dialects like Nghe An. This is due to our audio data containing only news anchor voices, and the news they are reading from contains only standardized scripts. Therefore, the audio are standardized language read in light tonal voices and meant to be easy to understand. For this reason, our next steps require us to find audios that are more heavy in dialect tones.
</p>
<p>
  <b>
  How easily are your results able to be reproduced by others?
  Did your dataset or annotation affect other people's choice of research or development projects to undertake?
  Does your work have potential harm or risk to our society? What kinds? If so, how can you address them?
  What limitations does your model have? How can you extend your work for future research?</p>
  </b>
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
  


<!--</body></html>-->
