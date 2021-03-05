# Catatan Seputar GIT

### setup SSH github permanent di ubuntu 

* Install ssh-client 

`sudo apt update && sudo apt install -y openssh-client git`

*  Membuat directory dan subdirectory tempat SSH keys kita  
```
mkdir -p ~/.ssh/github
chmod 700 ~/.ssh ~/.ssh/github
```

* Kita generate ssh keys kemudian kita beri permission `600`

`ssh-keygen -t rsa -b 4096 -C 'your@email.com' -f ~/.ssh/github/id_rsa -q -N ''`

* copy isi file di `id_rsa.pub` 

`gedit ~/.ssh/github/id_rsa.pub`

copy semua isi content `id_rsa.pub` dan masukan ke dalam `ssh keys di github`

![gambar example](https://i.stack.imgur.com/cCx8p.png)

* setelah selesai membuat kita buat file `~/.ssh/config` dan copy kedalam config yang telah kita buat dengan content berikut :  
```
Host github.com
    IdentityFile ~/.ssh/github/id_rsa
```

* kita lakukan test untuk tahap terakhir 

`ssh -T git@github.com`

jika muncul pesan berikut maka setup sudah selesai, dan kita sudah bisa remote otomatis dengan account github kita

`Hi deni! You've successfully authenticated, ...`
