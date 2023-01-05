## *PROXYパターン*  
Proxyパターンは、Client、Subjext、Proxy、RealSubjectのクラスからなるパターンである。  
Subjectは、Proxy、RealSubjectの共通インターフェースを定義する。
このSubjectのインターフェースをRealSubjectとProxyが実装する。ClientからRealSubjectへの要求があった場合に、まずはProxyで処理を行い、Clientに戻す。Proxyで処理出来なかった場合に、RealSubjectが処理する、といったデザインパターンとなっている。  
これによって、RealSubjectを変更することなく、前後に異なった処理を加えることができる。  
### ・使用例  
使用例の一つとしては、ウェブサイトのパスワード規制があげられる。RealSubjectをウェブサイトへのアクセスとして、Proxyをパスワード入力として実装すれば、パスワードを知らない人に入場を規制することができる。