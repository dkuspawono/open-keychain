[//]: # (注意：请把每个句子放在单独一行中， Transifex 将把每一行放置在独立的翻译表单内！)

## 密钥确认
在进行确认之前，您无法可靠地将一个密钥与特定人物关联起来。
确认密钥的最简单方式是扫描二维码或者通过NFC进行交换。
To confirm keys between more than two persons, we suggest using the key exchange method available for your keys.

## 密钥状态

<img src="status_signature_verified_cutout_24dp"/>  
已确认：您已经通过某种方式（例如扫描二维码）确认了这个密钥。  
<img src="status_signature_unverified_cutout_24dp"/>  
未确认：这个密钥尚未被确认。您无法确保这个密钥与特定人物的关联是可靠的。  
<img src="status_signature_expired_cutout_24dp"/>  
已过期：这个密钥不再有效。只有它的拥有者能扩展它的有效期。  
<img src="status_signature_revoked_cutout_24dp"/>  
已吊销：这个密钥不再有效。它已经被所有者声明为已吊销状态。

## 高级信息
OpenKeychain 中的“密钥确认”行为，是根据 OpenPGP 标准规定，通过创建认证实现的。
这个认证是一个 [“一般认证（0x10）”](http://tools.ietf.org/html/rfc4880#section-5.2.1) ，标准中的描述是：
“对于密钥持有者与密钥所示标识之间的关联，认证签发者不对其可靠性做出任何表态。”

习惯上，这些认证（也包括较高的信任等级，例如“正向认证” (0x13) ）是以 OpenPGP 的信任网络的形式存在的。
为了消除信任网络的可用性问题，我们的密钥确认模型采用一套相对简单的概念。
我们相信密钥的确认过程应该在不妨碍日常使用的情况下尽量可靠。
我们也不实现像 GnuPG 那样的（可传递）信任签名或信任数据库。
此外，当某密钥含有至少一个被信任密钥所认证过的用户标识时，它将在密钥列表中被标记为“已确认”。