## toC, toBのサービスを持つ自社開発企業

2022年10月〜

### 担当工程  
設計, コーディング, 運用/保守

### 経験した職種・役割
バックエンド,フロントエンド,インフラ

### 使用経験がある技術

#### 言語
- TypeScript

#### フロントエンド
- Next.js

#### バックエンド
- Express
- TypeORM, Prisma, Zod

#### インフラ
- AWS（EKS, Aurora MySQL, Cloud Watch など）
- Google Cloud（GKE, Cloud SQL など）
- Kustomize
- Pulumi
- Argo CD
- Datadog

#### 他
- Github Actions
- GitLab CI/CD
- Nx


### 経験したプロジェクトなど

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

#### サービスの運用/保守
【概要】  
自社ToCサービスの運用/保守。バックエンド、フロントエンドともに担当。  

【開発・実装内容や課題・問題点】  
- 新規機能追加、バグ修正  
- ライブラリのアップデートに伴うコード修正など

【課題解決方法・使用技術】  
- バックエンドはTypeScript+Express、クリーンアーキテクチャでDIを使用。  
- フロントエンドはTypeScript+Next.js。  

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

#### IaC導入
【概要】  
IaCを導入してインフラをコード管理  

【開発・実装内容や課題・問題点】  
- インフラ周りのドキュメントなどの整備がされておらずコード管理もされていなかったためIaCでのコード化を実施  

【課題解決方法・使用技術】  
- バックエンド、フロントエンドともにTypeScriptを使用しており、導入の敷居や今後の管理を考えるとPulumi（＋TypeScript）が適切だろうということで導入を決定した。  
- 既存インフラのアンチパターンを修正しつつPulumiに落とし込んだ。  

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

#### インフラ,k8s環境の移行・改善
【概要】  
EKS→GKE, RDS→Cloud SQL移行とGitOpsや新規モニタリングツール導入  

【開発・実装内容や課題・問題点】  
- 会社の方針でEKS→GKEへの移行。  
- k8sのCD手法がPush型だったためGitOpsを導入した。技術選定から実装までほぼ１人で実施した。  

【課題解決方法・使用技術】  
- メジャーなCDツールに目立った機能差はなかったため、GUIが優れているArgo CDを導入。  
- 環境の差分管理にはKustomizeを使用した。環境差分の管理のみに集中して、それ以外の共通化は行わないことで可読性を落とさないように工夫した。  
- k8s Secretの管理方法は選択肢が多かったが導入事例が若干多いように感じたExternal Secrets Operatorを導入した。（結果的にSecret管理はしやすかった）  
- GitOpsに合わせた（Docker imageタグなど）CI/CD構築。  
- モニタリングツールはDatadogを選定。分散トレーシングなどを導入した。  
- DeploymentのresourceやHPAのチューニングによるコスト抑制を実施。  
- Aurora→Cloud SQLへのDMSを使った移行。  
- Cloud SQL Auth Proxyを使ってGKEとCloud SQLの接続。

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

#### GitLab→GitHub移行
【概要】  
GitLabからGitHubへの移行  

【課題解決方法・使用技術】  
- GitHub ActionsでのCI/CD構築。  

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

#### Monorepo導入（進行中）
【概要】  
言語がTypeScriptで統一されているためMonorepoを導入  

【開発・実装内容や課題・問題点】  
- MonorepoツールはNxを使用。ツール選定や大まかな設計は上司と相談しつつ決定。コーディングは全て担当。  

【課題解決方法・使用技術】  
- DockerfileをMonorepoアプリ用に新規に作成。Multi-stage buildsを使ってimageサイズの軽量化を実施。  
- CIで複数のアプリケーションimageのbuildが必要なため、Github Actionsのmatrix strategyを利用して並列でbuildを行えるように設計。  

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

#### バックエンドのライブラリのリプレイス（進行中）  
【概要】  
Expressアプリで使用しているライブラリのリプレイス  

【開発・実装内容や課題・問題点】  
- TypeORMからPrismaへの移行。  
- フロント側でスキーマから生成された型を使いたかったがJoiを使用しているため実現不可だった。  

【課題解決方法・使用技術】  
- Zodを使用してスキーマからの型生成を可能にした。  
- Zodの型と既存の型の二重管理問題はzod-prisma-typesでPrismaの型からZodの型とスキーマを生成することにした。
