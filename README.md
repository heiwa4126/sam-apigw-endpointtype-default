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


# パンチライン

同じドキュメントの英語版
[EndpointConfiguration - AWS Serverless Application Model](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-property-api-endpointconfiguration.html)
では、デフォルト書いてない。

[Choose an endpoint type to set up for an API Gateway API - Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-endpoint-types.html)
では、デフォルトは `EDGE` と書かれている。

EDGEのほうが費用高いと思われるので(要確認)
REGIONALを明示したほうがいいかもしれない。
