  --------------------------------------------------------SISTEM TRAVEL MOBIL ANTAR KOTA KALTIM-----------------------------------------------------


1. Letak penerapan Abstraction (class/interface yang digunakan).


  a. Abstract Class: Travel

   - Travel dideklarasikan sebagai abstract class.
  
   - Di dalamnya ada method public abstract double hitungHargaTiket(); = Method ini harus dioverride oleh setiap subclass (EkonomiTravel, PremiumTravel).
  
   - Artinya, Travel hanya mendefinisikan “konsep umum travel”, sedangkan implementasi detail harga tiket diserahkan ke masing-masing subclass.

   - Abstraction di Travel (abstract class) & JumlahPenumpang (interface).


  b. Interface: JumlahPenumpang

   - Interface ini berisi kontrak setJumlahPenumpang(int jumlah) dan getJumlahPenumpang().
  
   - Class Travel mengimplementasikan interface ini, sehingga setiap subclass otomatis punya kewajiban untuk bisa mengatur jumlah penumpang.
  
  Jadi, Abstraction ada di abstract class Travel, interface JumlahPenumpang



  i. Di SubClass Travel.Java (Abstraction)
      
  Kode Program:

    public abstract class Travel implements JumlahPenumpang {
    private String sopir;
    private String asal;
    private String tujuan;
    private String tipeMobil;
    private int jumlahPenumpang;

    // Constructor
    public Travel(String sopir, String asal, String tujuan, String tipeMobil) {
        this.sopir = sopir;
        this.asal = asal;
        this.tujuan = tujuan;
        this.tipeMobil = tipeMobil;
    }




   ii. Di SubClass JumlahPenumpang.Java (interface)
  
   Kode Program: 
  
    public interface JumlahPenumpang {
      void setJumlahPenumpang(int jumlah);
      int getJumlahPenumpang();
    }



  
2. Letak penerapan Polymorphism Overriding.

     Polymorphism artinya satu method atau object bisa punya banyak bentuk. Di program ini, diterapkan lewat Overloading dan Overriding:

   - Overriding (Runtime Polymorphism)
  
   - Method hitungHargaTiket() ada di Travel sebagai abstract.
  
   - Lalu dioverride di EkonomiTravel, dan PremiumTravel  

  
     Polymorphism Overriding hitungHargaTiket() di EkonomiTravel dan PremiumTravel.
  
  
     i. Di SubClass Ekonomi.Java
  
     Kode Program:

         @Override
          public double hitungHargaTiket() {
              return hargaTiket * getJumlahPenumpang();
          }
      
          @Override
          public String toString() {
              return "[Ekonomi] " + super.toString() + ", Harga Persatu Tiket : Rp" + hargaTiket;
          }






   ii. Di SubClass Premium.Travel

   Kode Program:

        @Override
        public double hitungHargaTiket() {
            return hargaTiket * getJumlahPenumpang();
        }
    
        @Override
        public String toString() {
            return "[Premium] " + super.toString() + ", Harga Persatu Tiket: Rp" + hargaTiket;
        }
    


3. Letak penerapan Polymorphism Overloading.

     Overloading artinya kita membuat method dengan nama yang sama, tetapi parameternya berbeda (jumlah atau tipe data parameternya beda).

     Polymorphism Overloading tambahTravel() di service.

     i. Overloading 1 di SubClass Service.Java

     Kode Program:

           public void tambahTravel(Travel t) {
              daftarTravel.add(t);
          }




     ii. Overloading 2 di SubClass Service.Java

     Kode Program:

          public void tambahTravel(String sopir, String asal, String tujuan, String tipeMobil, boolean premium) {
            if (premium) {
                daftarTravel.add(new PremiumTravel(sopir, asal, tujuan, tipeMobil));
            } else {
                daftarTravel.add(new EkonomiTravel(sopir, asal, tujuan, tipeMobil));
            }
        

       

4. Hasil dari run program:

<img width="1018" height="157" alt="image" src="https://github.com/user-attachments/assets/f5107003-2600-4dd6-bf43-54d6672bd389" />



   
