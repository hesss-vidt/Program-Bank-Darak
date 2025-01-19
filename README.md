import os

# List untuk menyimpan data donor
data_nama = []
data_usia = []
data_no_telp = []
data_alamat = []
data_gol_darah = []
data_riwayat_penyakit = []

while True:
    os.system("cls")
    print("LAYANAN PALANG MERAH INDONESIA")
    print("==============================")
    print("Tentukan Identitas Anda")
    print("\n1. Admin")
    print("2. Pasien")
    print("3. Keluar\n")
    identitas = input("Silahkan Pilih Identitas Anda 1 atau 2 : ")
    
    # Menu untuk Admin
    if identitas == "1":
        while True:
            os.system("cls")
            print("\nProgram Bank Darah - Admin")
            print("=============================\n")
            print("1. Masukkan Data Donor")
            print("2. Cari Data Donor")
            print("3. Tampilkan Semua List Donor")
            print("4. Hapus Data Donor")
            print("5. Kembali ke Menu Identitas\n")
            
            pilihan = input("Silahkan Pilih Menu : ")
            
            # Menu Donor Darah
            if pilihan == "1":
                os.system("cls")
                nama = input("Masukkan Nama Pendonor: ").upper()
                usia = input("Masukkan Usia Pendonor : ")
                no_telp = input("Masukkan Nomor Telepon : ")
                alamat = input("Masukkan Alamat Pendonor : ")
                gol_darah = input("Masukkan Golongan Darah yang didonorkan (A/B/AB/O): ").upper()
                riwayat_penyakit = input("Apakah ada Riwayat Penyakit Menular (Ada/Tidak) : ")
                
                if gol_darah in ["A", "B", "AB", "O"]:
                    data_nama.append(nama)
                    data_usia.append(usia)
                    data_no_telp.append(no_telp)
                    data_alamat.append(alamat)
                    data_gol_darah.append(gol_darah)
                    data_riwayat_penyakit.append(riwayat_penyakit)
                    print("\nData donor berhasil ditambahkan!")
                else:
                    print("\nData tidak valid!")
                
                input("\nTekan Enter untuk kembali ke menu.")

            # Menu Cari Donor
            elif pilihan == "2":
                os.system("cls")
                gol_darah_dicari = input("Masukkan golongan darah pendonor yang dicari (A/B/AB/O): ").upper()
                
                print("-" * 111)
                print("| No. |          Nama Pendonor         |  Usia  |   Nomor Telepon   | Riwayat Penyakit |        Alamat          |")
                print("-" * 111)
                
                ditemukan = False
                for i in range(len(data_nama)):
                    if data_gol_darah[i] == gol_darah_dicari:
                        ditemukan = True
                        kolom1 = str(data_nama[i])
                        kolom2 = str(data_usia[i])
                        kolom3 = str(data_no_telp[i])
                        kolom4 = str(data_riwayat_penyakit[i])
                        kolom5 = str(data_alamat[i])
                        kolom6 = str(i + 1)

                        print("| " + kolom6 + (4 - len(kolom6)) * " "
                        + "| " + kolom1 + (31 - len(kolom1)) * " "
                        + "| " + kolom2 + (7 - len(kolom2)) * " "
                        + "|   " + kolom3 + (16 - len(kolom3)) * " "
                        + "|    " + kolom4 + (14 - len(kolom4)) * " "
                        + "|  " + kolom5 + (22 - len(kolom5)) * " " + "|")
                        print("-" * 111)

                if not ditemukan:
                    print("\nMaaf, donor dengan golongan darah tersebut tidak tersedia.")

                input("\nTekan Enter untuk kembali ke menu.")

            # Menu Tampilkan Semua Donor
            elif pilihan == "3":
                os.system("cls")
                if len(data_nama) > 0:
                    print("Daftar semua donor:")
                    print("=" * 20)
                    
                    print("-" * 128)
                    print("| No. |          Nama Pendonor         | Golongan Darah |  Usia  |   Nomor Telepon   | Riwayat Penyakit |        Alamat          |")
                    print("-" * 128)
                    
                    for i in range(len(data_nama)):
                        kolom1 = str(data_nama[i])
                        kolom2 = str(data_usia[i])
                        kolom3 = str(data_no_telp[i])
                        kolom4 = str(data_riwayat_penyakit[i])
                        kolom5 = str(data_alamat[i])
                        kolom6 = str(i+1)
                        kolom7 = str(data_gol_darah[i])

                        print ("| " + kolom6 + (4-len(kolom6))*" "
                        + "| " + kolom1 + (31-len(kolom1))*" "
                        + "|     " + kolom7 + (11-len(kolom7))*" "
                        + "|  " + kolom2 + (6-len(kolom2))*" "
                        + "|   " + kolom3 + (16-len(kolom3))*" "
                        + "|    " + kolom4 + (14-len(kolom4))*" "
                        + "| " + kolom5 + (22-len(kolom5))*" " + "|")
                        print ("-"*128)
                else:
                    print("\nTidak ada data donor yang tersimpan.")
                
                input("\nTekan Enter untuk kembali ke menu.")

            # Menu Hapus Donor
            elif pilihan == "4":
                os.system("cls")
                nama_hapus = input("Masukkan Nama Pendonor yang Ingin Dihapus: ").upper()
                
                ditemukan = False
                for i in range(len(data_nama)):
                    if data_nama[i] == nama_hapus:
                        ditemukan = True
                        data_nama.pop(i)
                        data_usia.pop(i)
                        data_no_telp.pop(i)
                        data_alamat.pop(i)
                        data_gol_darah.pop(i)
                        data_riwayat_penyakit.pop(i)
                        print("Donor berhasil dihapus.")
                        break  # Keluar dari perulangan jika donor ditemukan dan dihapus

                if not ditemukan:
                    print("Donor dengan nama tersebut tidak ditemukan.")
                
                input("\nTekan Enter untuk kembali ke menu.")
            
            # Kembali ke menu identitas
            elif pilihan == "5":
                break
            
            # Input tidak valid
            else:
                print("\nPilihan tidak valid! Silakan pilih kembali.")
                input("\nTekan Enter untuk kembali ke menu.")
    
    # Menu untuk Pasien
    elif identitas == "2":
        while True:
            os.system("cls")
            print("\nProgram Bank Darah - Pasien")
            print("==============================\n")
            print("1. Donorkan Darah")
            print("2. Cari Donor")
            print("3. Kembali ke Menu Identitas\n")
            
            pilihan = input("Silahkan Pilih Menu : ")
            
            # Menu Donor Darah
            if pilihan == "1":
                os.system("cls")
                nama = input("Masukkan Nama Pendonor: ").upper()
                usia = input("Masukkan Usia Pendonor : ")
                no_telp = input("Masukkan Nomor Telepon : ")
                alamat = input("Masukkan Alamat Pendonor : ")
                gol_darah = input("Masukkan Golongan Darah yang didonorkan (A/B/AB/O): ").upper()
                riwayat_penyakit = input("Apakah ada Riwayat Penyakit Menular (Ada/Tidak) : ")
                
                if gol_darah in ["A", "B", "AB", "O"]:
                    data_nama.append(nama)
                    data_usia.append(usia)
                    data_no_telp.append(no_telp)
                    data_alamat.append(alamat)
                    data_gol_darah.append(gol_darah)
                    data_riwayat_penyakit.append(riwayat_penyakit)
                    print("\nData donor berhasil ditambahkan! Silakan tunggu informasi lebih lanjut yang akan dikirim melalui nomor Anda.")
                else:
                    print("\nData tidak valid!")
                
                input("\nTekan Enter untuk kembali ke menu.")
            
            # Menu Cari Donor
            elif pilihan == "2":
                os.system("cls")
                gol_darah_dicari = input("Masukkan golongan darah yang dicari (A/B/AB/O): ").upper()
                
                print("-" * 111)
                print("| No. |          Nama Pendonor         |  Usia  |   Nomor Telepon   | Riwayat Penyakit |        Alamat          |")
                print("-" * 111)
                
                ditemukan = False
                for i in range(len(data_nama)):
                    if data_gol_darah[i] == gol_darah_dicari:
                        ditemukan = True
                        kolom1 = str(data_nama[i])
                        kolom2 = str(data_usia[i])
                        kolom3 = str(data_no_telp[i])
                        kolom4 = str(data_riwayat_penyakit[i])
                        kolom5 = str(data_alamat[i])
                        kolom6 = str(i+1)

                        print ("| " + kolom6 + (4-len(kolom6))*" "
                        + "| " + kolom1 + (31-len(kolom1))*" "
                        + "| " + kolom2 + (7-len(kolom2))*" "
                        + "|   " + kolom3 + (16-len(kolom3))*" "
                        + "|    " + kolom4 + (14-len(kolom4))*" "
                        + "|  " + kolom5 + (22-len(kolom5))*" " + "|")
                        print ("-"*111)

                if not ditemukan:
                    print("\nMaaf, donor dengan golongan darah tersebut tidak tersedia.")
                
                input("\nTekan Enter untuk kembali ke menu.")
            
            # Kembali ke menu identitas
            elif pilihan == "3":
                break
            
            # Input tidak valid
            else:
                print("\nPilihan tidak valid! Silakan pilih kembali.")
                input("\nTekan Enter untuk kembali ke menu.")
    
    elif identitas == "3" :
        print("\n Terima kasih telah menggunakan program Bank Darah Kami.")
        break
    # Input identitas tidak valid
    else:
        print("\nPilihan tidak valid! Silakan pilih kembali.")
        input("\nTekan Enter untuk kembali ke menu.")
