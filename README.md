# Pratikum8
RIDHO AKBAR PRATAMA

312210294/TI.B1.22

BAHASA PEMROGRAMAN

# Latihan OOP pada python menggunakan class dan menginstansiasi sebuah class lalu membuat program crud sederhana dengan class
1. Pertama kita buat folder pratikum8 disertai dengan file latihanoop.py

![Screenshot (224)](https://user-images.githubusercontent.com/115474016/206893849-b01e20c0-2150-4f5e-a50b-5193dd6aaef9.png)

2. Kita akan buat program crud sederhana dan berikut flowchart dan class diagram program yang akan dibuat.

flowchart :

![image](https://user-images.githubusercontent.com/115474016/206893400-72c86f31-f2f9-49ee-9507-c7d519b20abe.png)




class diagram :

![image](https://user-images.githubusercontent.com/115474016/206893941-7be94545-31ba-403a-ae84-a21168afd4e0.png)

3. lalu buka file latihanoop.py dan buat programnya seperti ini

                                          # import tabulate
                                          from tabulate import tabulate

                                          # RIDHO AKBAR PRATAMA
                                          # TI.22.B1

                                          # Membuat class dengan nama Mahasiswa


                                          class Mahasiswa:
                                               def __init__(self):
                                                   # membuat properti dataMahasiswa bertipe dictionary
                                                   self.dataMahasiswa = {
                                                       'No' : [],
                                                       'Nim' : [],
                                                       'Nama' : [],
                                                       'Tugas' : [],
                                                       'Uts' : [],
                                                       'Uas' : [],
                                                       'Nilai Akhir' : []
                                                   }

                                               # method untuk menampilkan data
                                               # self merupakan parameter untuk mengakses properti,
                                               def tampilkan(self):
                                                   print("Berikut data yang ada")
                                                   print(tabulate(self.dataMahasiswa, headers=[
                                                       'No', 'Nim' , 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

                                               # method untuk menmbahkan data

                                               def tambah(self, no):
                                                   # menginput data
                                                   nim = int(input("Masukkan NIM : "))
                                                   nama = input("Masukkan Nama : ")
                                                   tugas = int(input("Masukkan nilai tugas : "))
                                                   uts = int(input("Masukkan nilai UTS : "))
                                                   uas = int(input("Masukkan nilai UAS : "))
                                                   nilai_akhir = (tugas * 30 / 100) + (uts * 35 / 100) + (uas * 35 / 100)
                                                   # menambahkan data
                                                   self.dataMahasiswa['No'].append(no)
                                                   self.dataMahasiswa['Nim'].append(nim)
                                                   self.dataMahasiswa['Nama'].append(nama)
                                                   self.dataMahasiswa['Tugas'].append(tugas)
                                                   self.dataMahasiswa['Uts'].append(uts)
                                                   self.dataMahasiswa['Uas'].append(uas)
                                                   self.dataMahasiswa['Nilai Akhir'].append(nilai_akhir)
                                                   print('Data berhasil di tambahkan.')
                                                   # print(tabulate(dataMahasiswa, headers=[
                                                   #       'nim', 'nama', 'tugas', 'uts', 'uas', 'Nilai Akhir'], tablefmt="fancy_grid"))

                                               # method untuk mengedit data

                                               def ubah(self, nama):
                                                   # cek jika ada nama tersebut di dataMahasiswa
                                                   if nama in self.dataMahasiswa['Nama']:
                                                       # cari posisi indexnya lalu simpan di nimIndex
                                                       namaIndex = self.dataMahasiswa['Nama'].index(nama)
                                                       print("Pilih data yang mau di edit : ")
                                                       # perulangan mengedit data dalam bentuk pilihan
                                                       while True:
                                                           editApa = int(input(
                                                               "(1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai Uts, \n (5) Nilai Uas, \n (0) Save perubahan & exit \n : "))
                                                           print("")

                                                           if editApa == 1:
                                                               # merubah nim
                                                               newNim = int(input("Masukkan Nim :"))
                                                               self.dataMahasiswa['Nim'][namaIndex] = newNim
                                                           elif editApa == 2:
                                                               # merubah nama
                                                               newNama = input("Masukkan Nama :")
                                                               self.dataMahasiswa['Nama'][namaIndex] = newNama
                                                           elif editApa == 3:
                                                               # merubah nilai tugas dan nilai akhir
                                                               newTugas = int(input("Masukkan nilai tugas : "))
                                                               nilai_akhir = (newTugas * 30 / 100) + (self.dataMahasiswa['Uts'][namaIndex] * 35 / 100) + (
                                                                   self.dataMahasiswa['Uas'][namaIndex] * 35 / 100)
                                                               self.dataMahasiswa['Tugas'][namaIndex] = newTugas
                                                               self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                                                           elif editApa == 4:
                                                               # merubah nilai uts dan nilai akhir
                                                               newUts = int(input("Masukkan nilai Uts :"))
                                                               nilai_akhir = (self.dataMahasiswa['Tugas'][namaIndex] * 30 / 100) + (newUts * 35 / 100) + (
                                                                   self.dataMahasiswa['Uas'][namaIndex] * 35 / 100)
                                                               self.dataMahasiswa['Uts'][namaIndex] = newUts
                                                               self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                                                           elif editApa == 5:
                                                               # merubah nilaiuas dan nilai akhir
                                                               newUas = int(input("Masukkan nilai uas : "))
                                                               nilai_akhir = (self.dataMahasiswa['Tugas'][namaIndex] * 30 / 100) + (self.dataMahasiswa['Uts'][namaIndex] * 35 / 100) + (
                                                                   newUas * 35 /100)
                                                               self.dataMahasiswa['Uas'][namaIndex] = newUas
                                                               self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                                                           elif editApa == 0:
                                                               print('Perubahan data berhasil di simpan.')
                                                               break
                                                   else:
                                                       print('Data tidak di temukan.')

                                               # fungsi untuk menghapus data

                                               def hapus(self, nama):
                                                   if nama in self.dataMahasiswa['Nama']:
                                                       namaIndex = self.dataMahasiswa['Nama'].index(nama)
                                                       # menghapus data berdasarkan position index pada nama
                                                       del self.dataMahasiswa['No'][namaIndex]
                                                       del self.dataMahasiswa['Nim'][namaIndex]
                                                       del self.dataMahasiswa['Nama'][namaIndex]
                                                       del self.dataMahasiswa['Tugas'][namaIndex]
                                                       del self.dataMahasiswa['Uts'][namaIndex]
                                                       del self.dataMahasiswa['Uas'][namaIndex]
                                                       del self.dataMahasiswa['Nilai Akhir'][namaIndex]     
                                                       print("Data berhasil di hapus.")
                                                   else:
                                                       print("Data tidak di temukan.")

                                           # fungsi untuk mencari data


                                           # melkukan perulangan menggunakan while sampai user menekan huruf  Q perulangan akan
                                          no = 0
                                           # instansiasi class mahasiswa dengan nama instanceMhs
                                          instanceMhs = Mahasiswa()

                                           # melakukan perulangan sampai kondisi tertentu terpenuhi perulangan dan berhenti
                                          while True:
                                               # opsi input pilihan C,R,U,D,Q
                                               tanya = input(
                                                   "(C) Menambah data, \n (R) Melihat semua data, \n (U) Update data, \n (D) Menghapus data, \n (F) Mencari data, \n (Q) Keluar program : ")
                                               if tanya == "C":
                                                   # melakukan perulangan hingga user memilih n maka perulangan akan berhenti
                                                   while True:
                                                       no += 1
                                                       # memanggil fungsi tambah data dan memparsing data no
                                                       instanceMhs.tambah(no)
                                                       tambahDataLagi = input("Tambah data lagi ? (y/n) : ")
                                                       if tambahDataLagi == 'n':
                                                           break
                                                   # jika tanya == R maka lihat data
                                               elif tanya == "R":
                                                   # menampilan data dalam bentuk table menggunakan package tabulate
                                                   instanceMhs.tampilkan()
                                                   print("")
                                                   # jika tanya == U maka edit data
                                               elif tanya == "U":
                                                   print(tabulate(instanceMhs.dataMahasiswa, headers=[
                                                       'No', 'Nim', 'Nama', 'Tugas', 'Uts', 'Uas', 'Nilai Akhir'], tablefmt="fancy_grid"))
                                                   nama = input("Masukkan nama yang mau di edit : ")
                                                   print("")
                                                   instanceMhs.ubah(nama) 
                                                   # jika tanya == D maka hapus data
                                               elif tanya == "D":
                                                   print(tabulate(instanceMhs.dataMahasiswa, headers=[
                                                       'No', 'Nim', 'Nama', 'Tugas', 'Uts', 'Uas', 'Nilai Akhir'], tablefmt="fancy_grid"))
                                                   nama = input("Masukkan nama yang mau di hapus : ")
                                                   print("")
                                                   instanceMhs.hapus(nama) 
                                                   # jika tanya== Q maka keluar dari program
                                               elif tanya == "Q":
                                                   print("")
                                                   print("Anda telah keluar dari program.")
                                                   break

Dari perogram di atas memiliki beberapa opsi seperti C,R,U,D,Q:
- Ketika memiliki opsi C maka untuk menambah data
![Screenshot (225)](https://user-images.githubusercontent.com/115474016/206894166-810dcd66-1134-43cb-ad29-e40bdf0c7408.png)






- Ketika meiliki opsi R maka untuk melihat data
![Screenshot (226)](https://user-images.githubusercontent.com/115474016/206894174-93a3233e-b04a-4ae7-a576-cc1700c213da.png)





- ketika memilih opsi U maka untuk mengubah data yang dipilih

![Screenshot (227)](https://user-images.githubusercontent.com/115474016/206894198-487d5561-ddba-4f42-84a5-1fcec36d36d8.png)




- Ketika memilih data D maka untuk menghapus data yang dipilih
![Screenshot (228)](https://user-images.githubusercontent.com/115474016/206894206-00d94902-6c70-4d47-89d6-591ab58d6fde.png)



- Ketika memilih opsi Q maka untuk keluar program
 
![Screenshot (229)](https://user-images.githubusercontent.com/115474016/206894225-17408c51-f644-4a5b-8e9d-95e0286435a4.png)

                                                  
                                                  
                                                  
                                                  
                                                  
                                                  
                   











