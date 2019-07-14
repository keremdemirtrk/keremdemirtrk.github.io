---
layout: post
title:  "Aktif ve Pasif Bilgi Toplama"
date:   2019-07-15 18:34:10 +0700
categories: [security]
---

Öncelikle pasif toplamanın tanımını yaparak bu yazımıza giriş yapalım. Pasif toplama, hedef ile direkt olarak temasa geçilmeden bilgi toplama çeşidine denir. Bunu şöyle örnekleyebiliz, mesela suçlu sorgulamaları sırasındaki çarpraz sorgu çeşidi gibidir, yani bir kişiye diğer kişi hakkında sorular sorup bir şeyler öğrenmektir. Pentestler’de pasif bilgi toplama yapılacak işlem piramidinin en üstünde yer alır. Sırasıyla sistem ile ilgili bilgi edinilip, sınıflandırırız. Tabi bu bilgilerin toplanma çeşidi farklı yollardan sağlanabilir. 

Whois Sorgusu =>  Whois ip’nin ya da alan adının sahibinin kim olduğunu bulmamızı sağlar.

* www.archive.org => 1996’dan beri siteleri kayıt altına alan bir sistem.
* Netcraft => Sorgulanan ip adresi ya da alan adının çalıştığı işletim sistemi, web servisi olarak yazılan yazılım, son update bilgisine kadar birçok bilgiye erişebilirsiniz.
* Centralops => Pasif bilgi toplamada diğer önemli bir site olan Centralops’ın işlevi ip adresi bulma, detaylı whois bilgisi, dns kayıtı vb. bilgiler toplar.
* İpLocation => İp ya da alan adının hangi konumda çalıştırıldığını tespit eder.

AKTİF BİLGİ TOPLAMA

Hedef ile doğrudan iletişime geçilerek yapılan bilgi toplama işlemine denir. Tabi hedef ile doğrudan iletişim sağlandığı için daha net ve fazla sonuçlar elde ederiz. Tabi tek eksik yönü direk olarak temas olduğu için iz bırakılmış olur.(Firewall,IDS,Erişim Logları)

DNS ile Bilgi Toplama

DNS internet piramitimizin en alt basamağında yer alır, her şey burdan dallanır. İnternet aleminin 11880 ‘i diyebiliriz. DNS aracılığıyla çok bilgi edinebileceğimiz için kendi önerim DNS’lerin iyi yapılandırılmasıdır. Request (istek) mantığıyla çalışır. Nslookup linux ve windows için ortak dns sorgulama aracıdır. Ama ben dnsenum kullanıyorum. Ama dig denilen araç son zamanlarda daha popüler ve yakın zamanda Nslookup’ın yerini alıcak gibi gözüküyor. Bu yukarıda anlattığım toollar Kali-linux te hazır olarak bulunuyor. Fakat windows’a dair bir bilgim yok, MacOS sistemlerde iste sudo port aracılığıyla indirilebilir.

DNS SORGU TRAFİĞİNİ İZLEMEK

Ben bunu DİG aracıyla anlatacağım çünkü dediğim gibi daha popüler. Dig komutunu terminale yazınca zaten kullanma parametreleri çıkıyor, biz ise trafiği izlemek için “trace ” parametresini ekleyeceğiz. Bu parametre root’tan alan adımın bulunduğu yere kadar sunucu yolu belirler.

Bu trafiği izlemenin mantığı şöyle gerçekleşiyor, dediğim gibi DNS request tabanlı olduğu için ilk olarak resolv.conf dosyasından tanımlı olan DNS sunucundan ROOT DNS  listesini alıyor. Sonra bir sorgu gönderip gelen ilk DNS sunucundan sorumlu olan sunucuya sorar buradada zaten cevap alınır.

SUBDOMAİN TESPİTİ

Öncelikle subdomain demek bir alan adına bağlı onun alt sitesi diyebiliriz. Yani keremdemirtrk.com bir alan adı iken help.keremdemirtrk.com bir subdomain oluşturur. Bunu bulmak için de ben dnsmap kullanıyorum.


 BANNER YAKALAMA 

Yine banner’in ne olduğunu açıklıcam. Banner web sitelerindeki reklam panolarıdır ve eskiden beri güzel bir çalışan servisler hakkında bilgi toplama oltasıdır diyebiliriz. Telnet ile port’a bağlanarak yapılır. Biliyorsunuz ki en net bilgiler bir sistemin port’una bağlanarak elde edilir. Telnet kullanmak için ben ilkönce dnsenum kullanıp alan adından  ip adresine ulaşıp ordan da telnet aracılığıyla port taraması yapıyorum. Bunu görselli bir şekilde göstermeyeceğim ama kullanım şeklini belirtiyim.
			“telnet <ip adresi> <port>”

Bu yazının devamında ise Port Taramasına gireceğim orda Nmap kullanacağım için bir sonraki yazıma bırakıyorum. Teşekkürler…
						KEREM DEMİRTÜRK
