import matplotlib.pyplot as plt  # Mengimpor pustaka untuk visualisasi grafik

# Menetapkan judul dan label untuk sumbu x dan y
plt.title("Bresenham Algorithm")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")

def bres(x1, y1, x2, y2):
    # Menginisialisasi variabel
    x, y = x1, y1
    dx = abs(x2 - x1)  # Selisih x
    dy = abs(y2 - y1)  # Selisih y
    gradient = dy / float(dx)  # Menghitung gradien

    # Mengatur jika gradien lebih dari 1
    if gradient > 1:
        dx, dy = dy, dx  # Tukar dx dan dy
        x, y = y, x  # Tukar x dan y
        x1, y1 = y1, x1  # Tukar titik awal
        x2, y2 = y2, x2  # Tukar titik akhir

    p = 2 * dy - dx  # Inisialisasi nilai p
    print(f"x = {x}, y = {y}")  # Menampilkan titik awal

    # Inisialisasi daftar untuk menyimpan titik koordinat
    xcoordinates = [x]
    ycoordinates = [y]

    # Algoritma Bresenham untuk menggambar garis
    for k in range(2, dx + 2):
        if p > 0:  # Jika p positif
            y = y + 1 if y < y2 else y - 1  # Naik atau turun satu unit
            p = p + 2 * (dy - dx)  # Perbarui p
        else:
            p = p + 2 * dy  # Jika tidak, hanya perbarui p

        x = x + 1 if x < x2 else x - 1  # Naikkan atau turunkan x

        print(f"x = {x}, y = {y}")  # Menampilkan titik baru
        xcoordinates.append(x)  # Menambahkan ke daftar x
        ycoordinates.append(y)  # Menambahkan ke daftar y

    plt.plot(xcoordinates, ycoordinates)  # Menggambar garis
    plt.show()  # Menampilkan grafik

def main():
    # Meminta input pengguna untuk titik awal dan akhir
    x1 = int(input("Masukkan Nilai Awal X: "))
    y1 = int(input("Masukkan Nilai Awal Y: "))
    x2 = int(input("Masukkan Nilai Akhir x: "))
    y2 = int(input("Masukkan Nilai Akhir Y: "))

    bres(x1, y1, x2, y2)  # Memanggil fungsi bres untuk menggambar garis

if __name__ == "__main__":
    main()  # Menjalankan fungsi main
