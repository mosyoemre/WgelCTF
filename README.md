# Wgel CTF Çözümü

Merhabalar bu makalemde tryhackme platformundaki Wgel CTF makinesini çözeceğiz keyifli okumalar.

## 🔎 | Tarama

### NMAP

Herhangi bir açık bulabilmek için nmap ile port keşfi yapıyorum.

![nmap-scan1](https://media.discordapp.net/attachments/1284907420228784289/1284907537975476234/Nmap-tarama.png?ex=66e856e5&is=66e70565&hm=64325950ac8d802d178b0730f555f9f82210d53a9b2ddb3730353b437e7cfcba&=&format=webp&quality=lossless&width=237&height=37 "Nmap araması")

![nmap-scan2](https://media.discordapp.net/attachments/1284907420228784289/1284907538311024671/Nmap-tarama2.png?ex=66e856e5&is=66e70565&hm=fbde4e58fa4a50da9b816788091b4e278c84524568dfc5759b2686c39933caf9&=&format=webp&quality=lossless&width=268&height=26 "Tarama sonucu")

İşte! SSH ve HTTP servisinin varsayılan portlarının aktif olduğunu görüyoruz.

Herhangi bir detay için siteyi inceliyorum.

![site-index](https://media.discordapp.net/attachments/1284907420228784289/1284907537455644702/Index.png?ex=66e856e5&is=66e70565&hm=e5f0b971d7fa953b07d3745ee694f72e0e4e977e19475d4302da7f3f40a1edf3&=&format=webp&quality=lossless&width=647&height=595 "Site indexi")

Herhangi bir detay göremediğim için sitenin kaynak koduna bakıyorum.

![jessie](https://media.discordapp.net/attachments/1284907420228784289/1284907537753444483/Ipucu.png?ex=66e856e5&is=66e70565&hm=1a6f3d246406c1ab9f34acf2366197a30fd92e5ec11e36c2cfeb93dd65cd5984&=&format=webp&quality=lossless&width=279&height=12 "Jessie")

Siteyi geliştiren kişi arkadaşı için bir not bırakmış, bu ismi daha sonra kullanabiliriz, şimdilik aklımda tutuyorum.
### GOBUSTER

Sitede daha fazla detay bulabilmek için bir gobuster ile dizin araması yapıyorum.

![gobuster-scan1](https://media.discordapp.net/attachments/1284907420228784289/1284907554819801181/Gobuster-tarama.png?ex=66e856e9&is=66e70569&hm=a13c1e14bed1eedf955ad7a7bae28b8b9ae6d8280c559dbbb3c6a127af834f19&=&format=webp&quality=lossless&width=661&height=29 "Gobuster taraması")

![gobuster-result](https://media.discordapp.net/attachments/1284907420228784289/1284907554266284165/Gobuster-tarama2.png?ex=66e856e9&is=66e70569&hm=763681b3fa2d6c02ed485ca960ff6dae8015e8dc69c56e021513db7551237b49&=&format=webp&quality=lossless&width=505&height=52 "Tarama sonuçları")

Tarama sonucunda işe yarayabilecek bir dizin buldum. 
Indexinde işime yaramayan bir site var, yeni bulduğum dizin içerisinde yeni bir tarama yapıyorum.

![gobuster-scan2](https://media.discordapp.net/attachments/1284907420228784289/1284907554572599436/Gobuster-tarama3.png?ex=66e856e9&is=66e70569&hm=1f52a6ee23054abb4d61568bcefc7d461fcc9a2d42a661143fbf4cdcad3ab224&=&format=webp&quality=lossless&width=554&height=256 "2.tarama ve sonuçları")

Voila! SSH anahtarını içeren bir dizin buldum.

![ssh-key](https://media.discordapp.net/attachments/1284907420228784289/1284912747850760192/SSH_Key.png?ex=66e85bbf&is=66e70a3f&hm=6e21ccf5b5ab81d65fba1de7e2ae5ed0668aeecd141280671ffbc19cfa0fed3e&=&format=webp&quality=lossless&width=380&height=166 "SSH anahtarı")


## 🥷 | Sisteme Sızma

Bulduğum SSH anahtarını wget ile kali makineme çekiyorum.

![wget-ssh-key](https://media.discordapp.net/attachments/1284907420228784289/1284907540127289416/Wget.png?ex=66e856e5&is=66e70565&hm=3e709d2316ded40e9c2170d3d6ce8f370e54df9237cd108417c5900d9e58025d&=&format=webp&quality=lossless&width=691&height=156 "SSH anahtarını indiriyorum")

Sisteme girebilmemi sağlayacak bilgileri topladım, kullanıcı hariç... Daha önce sitenin kaynak kodunda bulduğum ismi kullanmayı deniyorum.

![ssh-connection](https://media.discordapp.net/attachments/1284907420228784289/1284919158555021344/SSH.png?ex=66e861b8&is=66e71038&hm=44169aadad22be8ff380f43a85846707ec45028c8d54b4c0d44f9239c03a71ab&=&format=webp&quality=lossless&width=403&height=180 "Sisteme giriş")

Başarılı! Sisteme başarıyla giriş yapıyorum.

## 🏳️ | Kullanıcı Flagini Bulma
Yetki yükseltmeden önce kullanıcı flagini buluyorum.
Kullanıcı flagini bulmak için dizinleri inceliyorum.

![user-flag](https://media.discordapp.net/attachments/1284907420228784289/1284907539770642453/User-flag.png?ex=66e856e5&is=66e70565&hm=53ddfaaaae8c9a1c1b4e640955e80e1c66aad9a781b1662cdb6fec891618e9af&=&format=webp&quality=lossless&width=283&height=64 "Kullanıcı flagi")

"Documents" dizininde "user_flag.txt" dosyasını bulup kullanıcı flagini tryhackme'e giriyorum.

## ❗ | Yetki Yükseltme ve Root Flagi
Son olarak makineyi bitirmek için yetki yükseltip root flagini buluyorum.

![wget-command](https://media.discordapp.net/attachments/1284907420228784289/1284907537178689616/Yetki.png?ex=66e856e5&is=66e70565&hm=ac7fda61d185ff70dcd758cf2690a7b8404ba168ed30b275d44f16d5617d77e1&=&format=webp&quality=lossless&width=722&height=87 "Açıklı komut")

Şifresiz bir şekilde yetkili çalıştırabileceğim bir komut bırakılmış, GTFOBins üzerinden exploit koduna bakıyorum.

![wget-exploitation](https://media.discordapp.net/attachments/1284907420228784289/1284907538667536557/PrivilegeEscalation.png?ex=66e856e5&is=66e70565&hm=267536683ff2607aa63d4e8b1e5bd666bd3e2128e512e609c12e2f41fe4398ef&=&format=webp&quality=lossless&width=644&height=200 "Yetki yükseltme kodu")

Bulduğum exploit ile kullanıcı flagini almak için kullandığım formatı deneyerek root flagini alıyor ve makineyi bitiriyorum.

![root-flag](https://media.discordapp.net/attachments/1284907420228784289/1284907539024056420/Root-Flag.png?ex=66e856e5&is=66e70565&hm=f3abac8c00264e53ce7e7fc930d6aa0922b0f833d28447cef44e43796bb255c7&=&format=webp&quality=lossless&width=715&height=52 "Root flagi")

## Sonuç
Bu makineden SSH anahtarının herkes tarafından ulaşılabilir bir yerde bırakmanın oldukça tehlikeli olduğunu anlıyoruz.
Böylelikle ilk makinemi başarıyla çözmüş oluyorum, buraya kadar okuduğunuz için teşekkür eder ve iyi günler dilerim.
