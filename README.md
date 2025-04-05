# ICML 2025 Submission 12437 Rebuttal Materials

||  MultiArith    | GSM8K    |  AddSub    |  AQuA  |  SingleEQ  |  SVAMP  |  MAWPS  |  Avg.  |
|-|-------------|-------------|-------------|-|-|-|-|-|
|**LIFT**| 98.66±0.71 | **49.03**±0.39 | 92.22±1.17  |**24.61**±1.29 | 95.62±0.29 |  63.15±1.00  |  **89.60**±0.46  |  **73.27**±0.45  |
|Full FT| 98.29±0.34 | 46.13±0.46 | **93.67**±0.47 | 22.34±1.66 |  96.01±0.56  |  61.93±1.21  |  89.50±0.89  |  72.55±0.50  |
|S2FT| **98.88**±0.52 | 45.05±0.94 | 92.78±0.73 | 23.62±0.28 |  **96.56**±0.95  |  59.2±0.60  |  89.39±0.46  | 72.21±0.45 |
|PiSSA| 98.17±0.41 | 43.78±0.54 | 93.04±0.66 | 24.11±1.23 |  96.06±0.24  |  59.25±0.86  |  89.60±0.75  | 72.00±0.14|
|DoRA| 97.54±0.79 | 46.97±0.76 | 91.46±0.37 | 22.93±1.32 |  93.16±0.56 |  62.65±0.72 |  88.13±1.24  |71.83±0.39 |
|LoRA| 97.17±0.47  | 47.02±1.19 | 91.01±0.46 | 24.31±2.00 |  93.21±0.53  |  **63.48**±0.61  |  87.61±0.70 |  71.97±0.18 |

*Table 8: Comparing different methods on LLaMA-2-7B fine-tuned on the MATH-10K dataset with four random seeds.*


<div style="display: flex; justify-content: space-between;">

  <div style="flex: 1; text-align: center;">
    <img src="./figures/memory/7b_1024.png" alt="Figure 1" width="300"/>
  </div>

  <div style="flex: 1; text-align: center;">
    <img src="./figures/memory/8b_1024.png" alt="Figure 2" width="300"/>
  </div>

</div>

<div style="margin-top: 10px; text-align: center;">
  <img src="./figures/memory/memory_legend.png" alt="Legend" width="600"/>
</div>

<p style="text-align: center; font-style: italic; margin-top: 10px;">
  <strong>Figure 17:</strong> Breakdown of memory consumption of Full Fine-tuning, LoRA, LIFT and LIFT_MLP on LLaMA-2-7B and LLaMA-3-8B.
</p>



<div style="margin-top: px; text-align: center;">
  <img src="./figures/loss_all.png" alt="Legend" width="400"/>
</div>

<p style="text-align: center; font-style: italic; margin-top: 10px;">
  <strong>Figure 18:</strong> Training loss curves of different methods with LLaMA-2-7B model on MATH-10K dataset.
</p>


<!-- Row 1: 3 figures -->
<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <img src="./figures/effective_rank/7B_q_proj_no_y.png" alt="Figure 1" style="width: 32%;"/>
  <img src="./figures/effective_rank/7B_k_proj_no_y.png" alt="Figure 2" style="width: 32%;"/>
  <img src="./figures/effective_rank/7B_v_proj_no_y.png" alt="Figure 3" style="width: 32%;"/>
</div>

<!-- Row 2: 2 figures -->
<div style="display: flex; justify-content: space-around; margin-bottom: 10px;">
  <img src="./figures/effective_rank/7B_up_proj_no_y.png" alt="Figure 4" style="width: 32%;"/>
  <img src="./figures/effective_rank/7B_down_proj_no_y.png" alt="Figure 5" style="width: 32%;"/>
</div>

<!-- Row 3: Wide legend -->
<div style="text-align: center; margin-top: 10px;">
  <img src="./figures/effective_rank/effective_rank_legend.png" alt="Legend" style="width: 90%; max-width: 800px;"/>
</div>

<!-- Optional unified caption -->
<p style="text-align: center; font-style: italic; margin-top: 10px;">
  <strong>Figure 19:</strong> Effective rank of the update matrix of different methods on LLaMA-2-7B.
</p>

|Rank|q_proj|k_proj|v_proj|up_proj|down_proj|
|-|-|-|-|-|-|
|**LIFT (Rank = 128)**|2469.63|2398.41|2811.06|3801.13|3943.63|
|Full FT|3952.63|3971.16|3977.38|4096.00|4096.000
|LoRA (Rank = 16)|16.00|16.00|16.00|16.00|16.00|
|LoRA (Rank = 128)|128.00|128.00|128.00|128.00|127.31|

*Table 9: The computed rank of weight update matrix for different method (we use 10x default threshold in computing the rank).*

|Effective Rank|q_proj|k_proj|v_proj|up_proj|down_proj|
|-|-|-|-|-|-|
|**LIFT (Rank = 128)**|1651.72|1565.29|1877.99|3012.28|3013.04|
|Full FT|3126.29|3121.36|3159.01|3787.20|3803.60|
|LoRA (Rank = 128)|111.72|113.84|112.90|126.30|120.84|
|PiSSA (Rank = 128)|649.03|659.42|702.99|874.21|855.92|
|HiRA (Rank = 128)|2356.04|2401.97|3075.19|3759.56|3689.39|
|HiRA (Rank = 512)|2518.85|2576.89|3079.04|3772.07|3690.66|

*Table 10: The effective rank of weight update matrix for different method.*

<div style="margin-top: px; text-align: center;">
  <img src="./figures/rank/7B_q_proj_diff_c.png" alt="Legend" width="400"/>
</div>

<p style="text-align: center; font-style: italic; margin-top: 10px;">
  <strong>Figure 20:</strong> Rank of update matrices under varying threshold-raising factors (LoRA rank = 16). The default threshold results in computed rank larger than target rank. As we increase the threshold-raising factor, the computed rank aligns with the target rank.
</p>

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <img src="./figures/rank/rank_10_7B_q_proj_no_y.png" alt="Figure 1" style="width: 32%;"/>
  <img src="./figures/rank/rank_10_7B_k_proj_no_y.png" alt="Figure 2" style="width: 32%;"/>
  <img src="./figures/rank/rank_10_7B_v_proj_no_y.png" alt="Figure 3" style="width: 32%;"/>
</div>

<!-- Row 2: 2 figures -->
<div style="display: flex; justify-content: space-around; margin-bottom: 10px;">
  <img src="./figures/rank/rank_10_7B_up_proj_no_y.png" alt="Figure 4" style="width: 32%;"/>
  <img src="./figures/rank/rank_10_7B_down_proj_no_y.png" alt="Figure 5" style="width: 32%;"/>
</div>

<!-- Row 3: Wide legend -->
<div style="text-align: center; margin-top: 10px;">
  <img src="./figures/rank/rank_legend.png" alt="Legend" style="width: 90%; max-width: 800px;"/>
</div>

<!-- Optional unified caption -->
<p style="text-align: center; font-style: italic; margin-top: 10px;">
  <strong>Figure 21:</strong> Rank of the update matrix of different methods on LLaMA-2-7B with 10x default threshold.
</p>