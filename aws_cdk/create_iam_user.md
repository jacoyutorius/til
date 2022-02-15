# IAM Userを作成する

```ts
import * as cdk from '@aws-cdk/core';
import * as iam from '@aws-cdk/aws-iam'

const bucketNameArn = "arn:aws:s3:::{ bucket name }";
const userNames = ["userA", "userB"];

// bucketNameArnに指定したバケットへファイルをアップロードする権限を持った
// IAMユーザーを作成する。
// @see https://tech.actindi.net/2019/08/16/090425
export class CdkStack extends cdk.Stack {
  constructor(scope: cdk.Construct, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    // ポリシーステートメントの定義
    const policyStatement = new iam.PolicyStatement({
      resources: [
        bucketNameArn,
        `${bucketNameArn}/*`
      ],
      actions: [
        "s3:PutObject",
        "s3:PutObjectAcl"
      ],
    })

    // ポリシーの定義
    const policyName = 'S3Uploadable';
    const policy = new iam.Policy(this, policyName, { 
      policyName,
      statements: [policyStatement],
    });

    // ユーザとアクセスキーの定義
    userNames.forEach((userName) => {
      const user = new iam.User(this, userName, { userName,  });
      const key = new iam.CfnAccessKey(this, `${userName}Key`, { userName: user.userName });
      new cdk.CfnOutput(this, `${userName}AccessKey`, { value: key.ref });
      new cdk.CfnOutput(this, `${userName}SecretAccessKey`, { value: key.attrSecretAccessKey });

      user.attachInlinePolicy(policy);
    })
  }
}
```