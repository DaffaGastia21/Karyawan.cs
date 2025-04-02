# Karyawan.cs
Tugas PBO THR
using System;

public class Karyawan
{
    private string nama;
    private string id;
    private double gajiPokok;

    public string Nama
    {
        get { return nama; }
        set { nama = value; }
    }

    public string ID
    {
        get { return id; }
        set { id = value; }
    }

    public double GajiPokok
    {
        get { return gajiPokok; }
        set { gajiPokok = value; }
    }

    public virtual double HitungGaji()
    {
        return gajiPokok;
    }

    public class KaryawanTetap : Karyawan
    {
        public override double HitungGaji()
        {
          return GajiPokok + 500000;
        }
    }

    public class KaryawanKontrak : Karyawan
    {
        public override double HitungGaji()
      {
            return GajiPokok - 200000;
      }
    }
    
    public class KaryawanMagang : Karyawan
    {
        public override double HitunganGaji()
        {
            return gajiPokok;
        }
    class Progam
    {
    static void Main(string[] args)
    }
        Console.WriteLine("Masukkan nama: ");
        string nama = Console.ReadLine();

        Console.WriteLine("Masukkan ID: ");
        string id = Console.ReadLine();

        Console.WriteLine("Masukkan gaji pokok: ");
        double gajiPokok;

        while (!double.TryParse(Console.ReadLine(), out gajiPokok) || gajiPokok < 0)
        {
            Console.WriteLine("Gaji pokok tidak valid. Masukkan angka positif: ");
        }

        Karyawan karyawan = null;


        switch (jenisKaryawan.ToLower())
        {
            case "tetap":
                karyawan = new KaryawanTetap();
                break;
            case "kontrak":
                karyawan = new KaryawanKontrak();
                break;
            case "magang":
                karyawan = new KaryawanMagang();
                break;
            default:
                Console.WriteLine("Jenis karyawan tidak valid.");
                return;
        }


        karyawan.Nama = nama;
        karyawan.ID = id;
        karyawan.GajiPokok = gajiPokok;

        Console.WriteLine($"Gaji Akhir untuk {karyawan.Nama} (ID: {karyawan.ID}) adalah: {karyawan.HitungGaji()}");
    }
  }
