# 前視角智慧桌球系統

## 關鍵字： `深度學習` `邊緣運算` `多線程處理` `幀差累積法`

<br>

---

### 站內連結：

<table style="width:1000px">
    <tr>
        <td align="center" width="165px">
            <a href="../">首頁與預覽</a><br>
        </td>
        <td align="center" width="165px">
            <a href="../work_1/">桌球3D軌跡<br>還原系統</a><br>
        </td>
        <td align="center" width="165px">
            <a href="../work_2/"><b>前視角智慧<br>桌球系統</b></a><br>
        </td>
        <td align="center" width="165px">
            <a href="../work_3/">強化學習之<br>模擬避障</a><br>
        </td>
        <td align="center" width="165px">
            <a href="../work_4/">音樂歌手辨識</a><br>
        </td>
    </tr>
</table>

<br>

---

## 作品簡介：

> > 此作品為**碩士論文**。<br>此作品為**進行中的產學合作計畫**，因此不會透漏實際完整模型架構與實現方法。
> 
> 本作品希望設計一款智慧桌球系統，結合發球機與手機端APP，讓旁觀者與使用者可以即時知道桌球打至的位置，也可以事後分析落球點統計數據，了解自己的打點，從而擬定訓練計畫。
> 
> ### 系統特色
>  - 建構於 NVIDIA® Jetson Nano™ 邊緣運算裝置
>  - 結合眾多演算法，包含：
>    - 幀差累計法 (進階幀差法應用)
>    - 輕量化深度神經網路模型
>    - 多線程平行運算
>  - 極快速的偵測模型，在邊緣運算裝置上高達 **20  FPS** 以上 ( NVIDIA® TITAN RTX™ 顯示卡上可達到 **400 FPS** 以上 )
> 
> ### 系統功能
>  - **球桌關鍵點偵測**，失準時可手動校正 (用以還原落球點位置，包含桌角與中線點等共6點)。
>  - **落球點偵測**，即時偵測打點並還原至虛擬球桌顯示。
>  - **虛擬球桌顯示**，即時顯示最新的打點與最近數球歷史打點。
>  - 其他功能由產學合作廠商端開發，包含發球機、手機端APP ... 。

<br>

**運行畫面 (gif動圖)：**

左: 原始影像與預測heatmap; 中: 幀差累積圖; 右: 落球位置還原，紅色為最新落球點，橘色為歷史落球點)

![image](gif/snapshot_work2.png)

<br>

**球桌偵測**

使用深度神經網路預測球桌的關鍵點(共6點)，再透過相機校正與轉換矩陣等運算，用於還原落球點在球桌上的位置。

![image](pic/table_detection.png)

<br>

**幀差累積法**

結合傳統影像處理的幀差法，發展出進階的**幀差累積法**，能夠顯現出桌球的移動軌跡，再從軌跡中找出落球點。

![image](pic/cumulative.png)

<br>

**深度模型預測**

透過深度神經網路(FCOS style network)來偵測幀差累積圖中是否有落球點與其位置。

![image](pic/heatmap.png)

<br>

**FCOS模型 (引用自: https://arxiv.org/abs/1904.01355)**

採用的神經網路為類似於FCOS的設計，並經過各式輕量化方式與平行處理來達成能在邊緣裝置上運作。

![image](pic/FCOS.png)

<br>

**更多落球點預測結果**

大多情況下，包含軌跡有斷點或畫面有雜訊，深度神經網路都能預測準確。

![image](pic/results.png)
    
<br>

---

<table >
    <tr>
        <td align="center" width="120px">
            <a href="#前視角智慧桌球系統">回到頂部</a><br>
        </td>
    </tr>
</table>