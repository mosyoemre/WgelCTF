# Wgel CTF Çözümü

Merhabalar bu makalemde tryhackme platformundaki Wgel CTF makinesini çözeceğiz keyifli okumalar.

## 🔎| Tarama

### NMAP

> Herhangi bir açık bulabilmek için nmap ile port keşfi yapıyorum.

![nmap-scan1](https://i.imgur.com/wNL7WEK.png "Nmap araması")

![nmap-scan2](https://i.imgur.com/8dKFEzn.png "Tarama sonucu")

> İşte! SSH ve HTTP servisinin varsayılan portlarının aktif olduğunu görüyoruz.

> Herhangi bir detay için siteyi inceliyorum.

![site-index](https://i.imgur.com/dNd7s6T.png "Site indexi")

> Herhangi bir detay göremediğim için sitenin kaynak koduna bakıyorum.

![jessie](https://i.imgur.com/fXECegL.png "Jessie")

> Siteyi geliştiren kişi arkadaşı için bir not bırakmış, bu ismi daha sonra kullanabiliriz, şimdilik aklımda tutuyorum.
### GOBUSTER

> Sitede daha fazla detay bulabilmek için bir gobuster ile dizin araması yapıyorum.

![gobuster-scan1](https://i.imgur.com/Zcj4QdJ.png "Gobuster taraması")

![gobuster-result](https://i.imgur.com/xNcPZ5d.png "Tarama sonuçları")

> Tarama sonucunda işe yarayabilecek bir dizin buldum. 
> Indexinde işime yaramayan bir site var, yeni bulduğum dizin içerisinde yeni bir tarama yapıyorum.

![gobuster-scan2](https://i.imgur.com/NFVFODf.png "2.tarama ve sonuçları")

> Voila! SSH anahtarını içeren bir dizin buldum.

![ssh-key](https://i.imgur.com/GhQYyKJ.png "SSH anahtarı")


## 🥷| Sisteme Sızma

> Bulduğum SSH anahtarını wget ile kali makineme çekiyorum.

![wget-ssh-key](https://i.imgur.com/TpZ2Xl7.png "SSH anahtarını indiriyorum")

> Sisteme girebilmemi sağlayacak bilgileri topladım, kullanıcı hariç... Daha önce sitenin kaynak kodunda bulduğum ismi kullanmayı deniyorum.

![ssh-connection](https://i.imgur.com/FXp6voc.png "Sisteme giriş")

> Başarılı! Sisteme başarıyla giriş yapıyorum.

## 🏳️| Kullanıcı Flagini Bulma
> Yetki yükseltmeden önce kullanıcı flagini buluyorum.
> Kullanıcı flagini bulmak için dizinleri inceliyorum.

![user-flag](https://i.imgur.com/S2pQ6GP.png "Kullanıcı flagi")

> "Documents" dizininde "user_flag.txt" dosyasını bulup kullanıcı flagini tryhackme'e giriyorum.

## ❗| Yetki Yükseltme ve Root Flagi
> Son olarak makineyi bitirmek için yetki yükseltip root flagini buluyorum.

![wget-command](https://i.imgur.com/LOnMBqj.png "Açıklı komut")

> Şifresiz bir şekilde yetkili çalıştırabileceğim bir komut bırakılmış, GTFOBins üzerinden exploit koduna bakıyorum.

![wget-exploitation](https://i.imgur.com/UuUCSs4.png "Yetki yükseltme kodu")

> Bulduğum exploit ile kullanıcı flagini almak için kullandığım formatı deneyerek root flagini alıyor ve makineyi bitiriyorum.

![root-flag](https://i.imgur.com/RPj3I2Z.png "Root flagi")

## 🎬| Çözüm Videosu

[![Çözüm Videosu](https://img.youtube.com/vi/mkvKyMeqorc/0.jpg)](https://www.youtube.com/watch?v=mkvKyMeqorc)

## Sonuç
> Bu makineden SSH anahtarının herkes tarafından ulaşılabilir bir yerde bırakmanın oldukça tehlikeli olduğunu anlıyoruz.
> Böylelikle ilk makinemi başarıyla çözmüş oluyorum, buraya kadar okuduğunuz için teşekkür eder ve iyi günler dilerim.
