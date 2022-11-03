# url_csv  
`url_array`に入っているAmazonのURLから
商品名と商品IDを取り出して
CSVファイルにするコード。  
CSVライブラリ・エンコード/デコードの練習。  

**※Amazonとは一切関係ありません。 **   

現状では新たにURLを渡してそのCSVを取得することはできません。  

## 苦労したところ  
ファイルを実行してもコンソールで何も起こらないので、
`puts`や`p`を入れたところ下記のようになった。  
`#<CSV`から始まるコンソールに出力されたこれらを見て
`CSV.open`の実行がうまく出来ていないのだと思い
デバッガ―を入れたりいろいろコードを変えてみたりしたが変わらず。  
**結局、実行はうまく行っていた。**  
ファイルがうまく作成できていないなら手動で用意する必要があると思い
`get_csv.rb`の親ディレクトリを見に行くと
`amazon_url.csv`が作成されており中身も期待通りだった。  
```  
# puts csv << [id, name]  
$ ruby get_csv.rb  
>>  
#<CSV:0x000056005acfd978>  

# p csv << [id, name]  
$ ruby get_csv.rb  
>>  
#<CSV io_type:File io_path:"amazon_url.csv" encoding:UTF-8 lineno:2 col_sep:"," row_sep:"\n" quote_char:"\"">  
```  

## メモ書き
実装のために書いていたメモの一部
```  
まずurlをeach文に入れる  
urlから商品名と商品idを取得する デコード  
どうやって取得する？https~.co.jp/と/dp/をカットする必要がある  
/でsplitして配列に入れるとか？  
slice sub  
取得したデータを変数に入れる？ハッシュにする？  
それらを使ってcsvとして出力する  
IDと商品名を別の変数にいれて、商品名だけをデコードする必要がある  
URIでうまくいかない時CGIを使うといいらしい  
もしくはforce_encoding('utf-8')  
```  