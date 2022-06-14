


# AsiaCommerce Test Frontend

  

## Installasi proyek

  

```bash

# install dependencies

$ npm install

  

# serve with hot reload at localhost:3000

$ npm run dev

  



```

  

For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

  

## Hal yang dilakukan ketika mengerjakan Frontend test AsiaCommerce

Hal yang saya lakukan ketika membuat projeknya yaitu menganalisa soal. Soal Frontend Test yaitu :

 1. ***Make VueJS 2 project boilerplate***
	 Di bagian soal ini saya memakai NUXT JS, walaupun saya belum pahan tentang Boilerplate. Tapi saya asumsikan memakai NUXT JS dengan Framework Bootstrap.
 2. ***Create pages and make any simply CRUD with local state only.***
 Di bagian soal nomer 2 saya masih tidak paham dengan namanya local state only. Tapi saya asumsikan local state only itu seperti project yang menggunakan `export default`.
 3. ***Create pages and fetch any api data from  *https://jsonplaceholder.typicode.com then display data* .***
 Dibagian soal nomer 3 ada 6 resources API yang bisa digunakan untuk test ini. Saya memilih di bagian **users** karena ada referensi CRUD beserta tampilannya.
 4. ***Creote “Button” component. Every ”Button” what you used, must be isolated as reusable component* .***
 Dari pengalaman saya, saya pernah menggunakan component untuk 1 fitur website. Dalam soal ini saya asumsikan desain Button ke dalam component. Kemudian memanggil `method` dalam parent.

# Tahapan pengerjaan Frontend Test AsiaCommerce
Saya mengerjakan test ini selama 3 hari mulai dari sabtu sampai senin dan saya banyak hal baru pada saat mengerjakan test ini.
## Pengerjaan Test hari sabtu 12 Juni 2022
Hal yan saya lakukan ialah mendapatkan data dari https://jsonplaceholder.typicode.com/users menggunakan `axios` dan menampilkan data berupa table
![enter image description here](https://i.imgur.com/4AY79g0.jpg)
Gambar diatas merupakan code untuk mengambil data dari https://jsonplaceholder.typicode.com/users. Dan hasil dari code tersebut ialah tampilan dibawah ini
![enter image description here](https://i.imgur.com/z8b7eTF.jpg)
## Pengerjaan Test hari minggu 13 juni 2022
di hari saya menambahkan input pada data dan juga menambahkan beberapa button seperti **Add user,** **Update User**, dan **Delete User**. Bisa dilihat di garis merah.
![enter image description here](https://i.imgur.com/bK0HUN6.jpg)
Tidak hanya itu saja. Saya menambahkan fungsi pada **Add Button** untuk bisa menambahkan user pada tabel.
![enter image description here](https://i.imgur.com/C506MZA.jpg)
*Contoh gambar sebelum ditambahkan user*
![enter image description here](https://i.imgur.com/j7hA0sW.jpg)
*Contoh gambar setelah ditambahkan user*
Dan untuk code pada fungsi add ada dibawah ini beserta button yang terhubung pada `submitUser()`

![enter image description here](https://i.imgur.com/xl6rwZC.jpg)
![enter image description here](https://i.imgur.com/qLQp5yw.jpg)
## Pengerjaan Test hari senin 14 juni 2022
Di hari ini saya berencana membuat modal pada update, membuat fungsi delete, dan juga component. Hal yang saya lakukan ialah membuat modal pada update. Sebenarnya saya memiliki halangan di bagian ini karena modal yang versi Bootstrap itu tidak bisa mengeluarkan modal. Sehingga secara terpaksa saya menggunakan Bootstrap dengan versi Vue atau Boostrap Vue. Bootstrap vue sama saja seperti bootstrap namun yang berbeda dari Bootstrap originalnya ialah dari tagnya.

    <template>
      <div>
        <b-button id="show-btn" @click="showModal">Open Modal</b-button>
        <b-button id="toggle-btn" @click="toggleModal">Toggle Modal</b-button>
    
        <b-modal ref="my-modal" hide-footer title="Using Component Methods">
          <div class="d-block text-center">
            <h3>Hello From My Modal!</h3>
          </div>
          <b-button class="mt-3" variant="outline-danger" block @click="hideModal">Close Me</b-button>
          <b-button class="mt-2" variant="outline-warning" block @click="toggleModal">Toggle Me</b-button>
        </b-modal>
      </div>
    </template>
    
    <script> export default {
        methods: {
          showModal() {
            this.$refs['my-modal'].show()
          },
          hideModal() {
            this.$refs['my-modal'].hide()
          },
          toggleModal() {
            // We pass the ID of the button that we want to return focus to
            // when the modal has hidden
            this.$refs['my-modal'].toggle('#toggle-btn')
          }
        }
      } </script>
*Contoh code untuk modal dari Bootstrap Vue*
```html
<div class="modal" tabindex="-1" role="dialog">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <p>Modal body text goes here.</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-primary">Save changes</button>
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
```
*Contoh code untuk modal dari Bootstrap*
Karena saya Bootstrap Vue bisa dijalankan baik ketimbang originalnya maka saya gunakan modal dari Bootstrap Vue. Dan hasil tampilan Modal dari Bootstrap Vue ialah seperti gambar dibawah ini.
![enter image description here](https://i.imgur.com/XtpsN0o.jpg)
Proses dari update user ke modal ialah

 1. Ambil array dari array utama
 2. Dikirim ke array temporary 
 3. Di tampilkan di input Update Data

Setelah mengganti atau mengedit user di modal akan ada tombol Update User yaitu untuk mengganti array yang sudah di edit di modal ke array utama. 
![enter image description here](https://i.imgur.com/rQKiF8T.png)
Untuk code yang digunakan ialah seperti gambar dibawah ini beserta button yang tersambung
![enter image description here](https://i.imgur.com/XgIvvuc.jpg)
*Contoh Button yang tersambung Update user![*C*](https://i.imgur.com/aevYPpf.jpg)*Contoh Button submit untuk user yang telah di edit
![enter image description here](https://i.imgur.com/IRboGBt.jpg)

*Contoh gambar untuk fungsi atau method*

Setelah penjelasannya dari update kemudian penjelasan dari bagian **Delete**. Delete button merupakan untuk delete user yang ada di tabel
![enter image description here](https://i.imgur.com/YaDfKHZ.png)

*Contoh gambar fungsi delete*
![enter image description here](https://i.imgur.com/rCypk5h.jpg)
![enter image description here](https://i.imgur.com/CiI9xDF.jpg)
*Contoh fungsi delete beserta button terhubung.*

Setelah penjelasan delete berikutnya ialah Button Component. Button component dalam projek ini ada 3 yaitu **AddUserButton** , **UpdateUserButton**, **DeleteUserButton**

![enter image description here](https://i.imgur.com/rllA0Vt.jpg)

*Contoh gambar file button component*

dan tidak hanya itu saja melainkan isi dari component tersebut ialah button untuk bisa di reusable
![enter image description here](https://i.imgur.com/hmbEnxE.jpg)

*Contoh is file component tiap button*
Dan untuk import ada di gambar bawah ini
![enter image description here](https://i.imgur.com/llIsLQP.jpg)

*Contoh file import component*
Untuk pemanggilannya ada di gambar sebelumnya seperti **add**, **update**, dan **delete**. 

Sekian dari penjelasan proyek ini semoga bermanfaat dan membantu.