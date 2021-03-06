+++
title = "Auto Scalingグループの動的スケーリング"
weight = 140
+++

動的スケーリングを設定する場合は、需要の増減に応じてスケールする方法を定義する必要があります。たとえば、現在 2 つのインスタンスで実行されているウェブアプリケーションがあり、アプリケーションの負荷が変化しても Auto Scaling グループの CPU 使用率を約 50% に維持する必要があるとします。これにより、過剰な量のアイドルリソースを維持することなくトラフィックの急上昇を処理するための追加の容量が得られます。このニーズを満たすため、自動的にスケーリングするように Auto Scaling グループを設定できます。ポリシータイプによって、スケーリングアクションがどのように実行されるかが決まります。 

ターゲット追跡スケーリングポリシーでは、スケーリングメトリクスを選択してターゲット値を設定します。Amazon EC2 Auto Scaling はスケーリングポリシーをトリガーする CloudWatch アラームを作成および管理し、メトリクスとターゲット値に基づいてスケーリング調整値を計算します。スケーリングポリシーは、指定されたターゲット値、またはそれに近い値にメトリクスを維持するために、必要に応じて容量を追加または削除します。ターゲット追跡スケーリングポリシーは、メトリクスをターゲット値に近い値に維持することに加えて、変化するロードパターンによるメトリクスの変化に適応します。 

1. **asg-automatic-scaling.json**ファイルを開き、スケーリングポリシーとして設定される内容を確認します。ファイルの内容変更は不要です。次のコマンドでスケーリングポリシーを設定します。

	```
	aws autoscaling put-scaling-policy --cli-input-json file://asg-automatic-scaling.json
	```

1. [Auto Scalingコンソール](https://console.aws.amazon.com/ec2/autoscaling/home#AutoScalingGroups:view=details)を開き、「スケーリングポリシー」タブから設定を確認します。
