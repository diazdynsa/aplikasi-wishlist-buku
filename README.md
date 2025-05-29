wishlist = []  # Daftar kosong untuk menyimpan wishlist buku

# Fungsi untuk menambahkan buku ke wishlist
def tambah_buku(judul):
    wishlist.append({"judul": judul, "sudah_dibaca": False})  # Menambahkan buku sebagai dictionary dengan status belum dibaca

# Fungsi untuk menampilkan semua buku dalam wishlist
def tampilkan_wishlist():
    if not wishlist:  # Jika daftar wishlist kosong
        print("Wishlist kosong.")  # Menampilkan pesan bahwa wishlist kosong
        return
    for i, buku in enumerate(wishlist):  # Iterasi melalui wishlist dengan indeks
        status = "Sudah dibaca" if buku["sudah_dibaca"] else "Belum dibaca"  # Menentukan status buku
        print(f"{i+1}. {buku['judul']} - {status}")  # Menampilkan daftar buku dengan statusnya

# Fungsi untuk menandai buku sebagai sudah dibaca
def tandai_sudah_dibaca(index):
    if 0 <= index < len(wishlist):  # Memastikan indeks valid
        wishlist[index]["sudah_dibaca"] = True  # Mengubah status buku menjadi sudah dibaca
    else:
        print("Index tidak valid.")  # Menampilkan pesan jika indeks tidak valid

# Fungsi untuk menghapus buku dari wishlist berdasarkan indeks
def hapus_buku(index):
    if 0 <= index < len(wishlist):  # Memastikan indeks valid
        del wishlist[index]  # Menghapus buku dari wishlist
    else:
        print("Index tidak valid.")  # Menampilkan pesan jika indeks tidak valid

# Fungsi untuk mengurutkan buku dalam wishlist berdasarkan judul 
def urutkan_berdasarkan_judul():
    wishlist.sort(key=lambda buku: buku["judul"].lower())  # Mengurutkan berdasarkan judul dalam huruf kecil

# Fungsi untuk menampilkan menu interaktif
def menu():
    while True:
        print("\n=== Aplikasi Book Wishlist ===") 
        print("1. Tambah buku ke wishlist")  
        print("2. Tampilkan wishlist") 
        print("3. Tandai buku sebagai sudah dibaca") 
        print("4. Hapus buku dari wishlist")  
        print("5. Urutkan berdasarkan judul")  
        print("0. Keluar") 

        pilihan = input("Pilih menu: ")  # Meminta input dari pengguna

        if pilihan == "1":  # Jika memilih opsi 1
            judul = input("Masukkan judul buku: ")  # Meminta judul buku dari pengguna
            tambah_buku(judul)  # Menambahkan buku ke wishlist
        elif pilihan == "2": 
            tampilkan_wishlist()  # Menampilkan daftar wishlist
        elif pilihan == "3":  
            tampilkan_wishlist()  # Menampilkan daftar wishlist
            idx = int(input("Pilih nomor buku yang sudah dibaca: ")) - 1  # Meminta input indeks buku
            tandai_sudah_dibaca(idx)  # Menandai buku sebagai sudah dibaca
        elif pilihan == "4":  
            tampilkan_wishlist()  # Menampilkan daftar wishlist
            idx = int(input("Pilih nomor buku yang ingin dihapus: ")) - 1  # Meminta input indeks buku
            hapus_buku(idx)  # Menghapus buku dari wishlist
        elif pilihan == "5":  
            urutkan_berdasarkan_judul()  # Mengurutkan daftar berdasarkan judul
            print("Wishlist berhasil diurutkan.")  # Memberikan konfirmasi
        elif pilihan == "0":  
            print("Terima kasih telah menggunakan aplikasi.")  # Menampilkan pesan keluar
            break  # Keluar dari loop
        else:
            print("Pilihan tidak valid.")  # Menampilkan pesan jika input tidak sesuai


menu()  # Memulai aplikasi
