<template>
  <div class="hello">
    <h1 :class="[score > 1 ? 'diatasKKM' : 'dibawahKKM']">Score : {{ score }}</h1>
    <h2 v-if="score > 6" style="color:green;">Berhasil, kamu luar biasa</h2>
    <h2 v-else style="color:red;">Kamu Gagal, ayo jangan cepat menyerah</h2>
    <div v-for="(soal, kumpulansoal) in questions">
      <h2>{{kumpulansoal+1}}. {{soal.deskripsi}} </h2>
      <div v-for="(pilihans, kumpulanpilihan) in soal.pilihan">
        <input type="radio" @click="checkAnswer(kumpulansoal, kumpulanpilihan)" :value="pilihans[0]" :name="kumpulansoal">
        <span v-text="pilihans[0]"></span>
      </div>
    </div>
  </div>
</template>

<script>

import Soal from '@/components/soal'
export default {
  name: 'HelloWorld',
  components:{
    Soal
  },
  data () {
    return {
      score: 0,
      answertrue : [],
      answerfalse : [],
      questions : [
        {
          deskripsi : "Kapan Indonesia Merdeka ?",
          pilihan : [
            ["1990"],
            ["2019"],
            ["1845"],
            ["1945", true]
          ]
        },
        {
          deskripsi : "Apa Ibu Kota Indonesia ?",
          pilihan : [
            ["Manila"],
            ["Jakarta", true],
            ["Kuala Lumpur"],
            ["Berlin"]
          ]
        },
        {
          deskripsi : "Apa Kepanjangan Dari Tugu BLA ?",
          pilihan : [
            ["Tugu Bandung Lautan Api", true],
            ["Tugu Bandung Lapangan Api"],
            ["Tugu Balikpapan Lautan Api"],
            ["Tugu Berlin Lautan Api"]
          ]
        },
        {
          deskripsi : "Tanggal 17 Agustus Adalah Hari Peringatan ?",
          pilihan : [
            ["Libur Nasional"],
            ["Sumpah Pemuda"],
            ["Kemerdekaan Indonesia", true],
            ["Idul Fitri"]
          ]
        },
        {
          deskripsi : "Apa Mata Uang Indonesia ?",
          pilihan : [
            ["Yen"],
            ["Euro"],
            ["Dollar"],
            ["Rupiah", true]
          ]
        },
        {
          deskripsi : "Siapa Presiden Indonesia Ke 2?",
          pilihan : [
            ["Soekarno"],
            ["Jokowi"],
            ["SBY"],
            ["Soeharto", true]
          ]
        },
        {
          deskripsi : "Mana Yang Bukan Termasuk Bahasa Daerah Indonesia?",
          pilihan : [
            ["Latin", true],
            ["Sunda"],
            ["Jawa"],
            ["Batak"]
          ]
        },
        {
          deskripsi : "Apa Bandara Terbesar Di Jakarta ?",
          pilihan : [
            ["Halim Perdana Kusuma"],
            ["Leuwi Panjang"],
            ["Soekarno Hatta", true],
            ["Husein"]
          ]
        },
        {
          deskripsi : "Apa Nama Bahasa Daerah Di Jawa Barat?",
          pilihan : [
            ["Sunda",true],
            ["Batak"],
            ["Isyarat"],
            ["Inggris"]
          ]
        },
        {
          deskripsi : "Apa Warna Bendera Indonesia?",
          pilihan : [
            ["Hijau"],
            ["Merah Putih", true],
            ["Hitam"],
            ["Kuning Putih"]
          ]
        },
      ]
    }
    },

    methods: {

      checkAnswer(kumpulansoal, kumpulanpilihan) {
        if(this.questions[kumpulansoal].pilihan[kumpulanpilihan][1]){
          if(this.answertrue.indexOf(kumpulansoal) == -1){
            this.answertrue.push(kumpulansoal);
          }
          if(this.answerfalse.indexOf(kumpulansoal) != -1){
            this.answerfalse.splice(this.answerfalse.indexOf(kumpulansoal),1);
          }
        }else{
          if(this.answertrue.indexOf(kumpulansoal) != -1){
            this.answertrue.splice(this.answertrue.indexOf(kumpulansoal),1);
            this.answerfalse.push(kumpulansoal);
          }else if(this.answerfalse.indexOf(kumpulansoal) != -1){

          }else{
            this.answerfalse.push(kumpulansoal);
          }
        }
        this.score = this.answertrue.length;
    }
  }
}
</script>
