# sam-apigw-typedefault

SAMのREST APIのエンドポイントタイプのデフォルト値が
[DomainConfiguration - AWS Serverless Application Model](https://docs.aws.amazon.com/ja_jp/serverless-application-model/latest/developerguide/sam-property-api-domainconfiguration.html)
だと `REGIONAL` となってるのだが、これがどうも怪しいのでテストしてみた。

自分の今の環境だと デフォルトでは `EDGE` になるんだけど...

Python 3.8。中身は"Hello world"を出すだけです。


# デプロイ

```sh
sam build
sam deploy --guided  # --guidedは最初の1回
```

`sam deploy --guided` は以下の

```
HelloWorldFunction may not have authorization defined, Is this okay? [y/N]: y
```

以外はデフォルトでいいです。


# スタックの削除

```sh
sam delete --no-prompts
```
で消えます。
