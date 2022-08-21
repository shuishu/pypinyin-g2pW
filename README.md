# pypinyin-g2pW

基于 [g2pW 0.0.6](https://github.com/GitYCC/g2pW/tree/v0.0.6) 提升 [pypinyin](https://github.com/mozillazg/python-pinyin) 的准确性。

优点：可以通过训练模型的方式提升拼音准确性。

缺点：依赖比较多，执行速度比较慢。


## 使用

### 安装依赖

1. 安装 [PyTorch](https://pytorch.org/get-started/locally/)。
2. 下载并解压 G2PWModel:

    ```
    mkdir G2PWModel
    cd G2PWModel
    wget https://storage.googleapis.com/esun-ai/g2pW/G2PWModel-v2.zip
    unzip G2PWModel-v2.zip
    cd ../
    ```
3. 安装 [git-lfs](https://git-lfs.github.com/)。
4. 下载 [bert-base-chinese](https://huggingface.co/bert-base-chinese):

   ```
   git lfs install
   git clone https://huggingface.co/bert-base-chinese
   ```
5. 安装本项目:

   ```
   pip install pypinyin-g2pw
   ```

### 使用示例

   ```python
   >>> from pypinyin import Style
   >>> from pypinyin_g2pw import G2PWPinyin

   # 需要将 model_dir 和 model_source 的值指向下载的模型数据目录
   >>> g2pw = G2PWPinyin(model_dir='G2PWModel/G2PWModel-v2/',
                     model_source='bert-base-chinese/',
                     v_to_u=False, neutral_tone_with_five=True)
   >>> han = '然而，他红了20年以后，他竟退出了大家的视线。'
   >>> g2pw.lazy_pinyin(han, style=Style.TONE)
   ['rán', 'ér', '，', 'tā', 'hóng', 'le', '20', 'nián', 'yǐ', 'hòu', '，', 'tā', 'jìng', 'tuì', 'chū', 'le', 'dà', 'jiā', 'de', 'shì', 'xiàn', '。']
   >>> g2pw.lazy_pinyin(han, style=Style.TONE3)
   ['ran2', 'er2', '，', 'ta1', 'hong2', 'le5', '20', 'nian2', 'yi3', 'hou4', '，', 'ta1', 'jing4', 'tui4', 'chu1', 'le5', 'da4', 'jia1', 'de5', 'shi4', 'xian4', '。']
   ```

## 模型训练

详见 [g2pW](https://github.com/GitYCC/g2pW/tree/v0.0.6) 官方文档中的说明。
