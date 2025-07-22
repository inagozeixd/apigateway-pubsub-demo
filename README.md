## 概要

API GatewayのAWS統合を活用したPub/Subデモ  

## 使い方

1. `git clone https://github.com/inagozeixd/apigateway-pubsub-demo.git`

2. `aws cloudformation deploy --template-file before_template.yaml --stack-name apigateway-pubsub-demo --capabilities CAPABILITY_NAMED_
IAM`

3. `aws cloudformation describe-stacks --stack-name apigateway-pubsub-demo --region ap-northeast-1 --query 'Stacks[0].Outputs'`

4. `3.`で表示される`OutputValue`をエンドポイントごとに控える

5. `curl -X POST https://hgo8s4ddyh.execute-api.ap-northeast-1.amazonaws.com/dev/message1 -H "Content-Type: application/json" -d '{"message": "queue1"}'`

6. `curl -X POST https://hgo8s4ddyh.execute-api.ap-northeast-1.amazonaws.com/dev/message1 -H "Content-Type: application/json" -d '{"message": "queue2"}'`

7. `curl -X POST https://hgo8s4ddyh.execute-api.ap-northeast-1.amazonaws.com/dev/message2 -H "Content-Type: application/json" -d '{"message": "hello"}'`

8. Cloudwatch Logsでログを確認して、振り分け先のLambdaが実行されていることを確認