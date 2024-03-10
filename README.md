// “menambahkan implementasi dengan table-driven”
using System;
using System.Collections.Generic;

class KodePos
{
    private Dictionary<string, string> kodePosTable;

    public KodePos()
    {
        // Inisialisasi tabel kode pos
        kodePosTable = new Dictionary<string, string>
        {
            {"Batununggal", "40266"},
            {"Kujangsari", "40287"},
            {"Mengger", "40267"},
            {"Wates", "40256"},
            {"Cijaura", "40287"},
            {"Jatisari", "40286"},
            {"Margasari", "40286"},
            {"Sekejati", "40286"},
            {"Kebonwaru", "40272"},
            {"Maleer", "40274"},
            {"Samoja", "40273"}
        };
    }

    public string GetKodePos(string kelurahan)
    {
        // Mengambil kode pos dari tabel
        if (kodePosTable.ContainsKey(kelurahan))
        {
            return kodePosTable[kelurahan];
        }
        else
        {
            return "Kode Pos Tidak Ditemukan";
        }
    }
}

class Program
{
    static void Main()
    {
        // Membuat instance dari class KodePos
        KodePos kodePosObject = new KodePos();

        // Meminta pengguna untuk memasukkan kelurahan
        Console.Write("Masukkan nama kelurahan: ");
        string kelurahan = Console.ReadLine();

        // Memanggil method getKodePos untuk kelurahan yang dimasukkan pengguna
        Console.WriteLine($"Kode Pos untuk {kelurahan}: {kodePosObject.GetKodePos(kelurahan)}");
    }
}

//“menambahkan implementasi dengan state-based construction”

using System;

class DoorMachine
{
    // Enum untuk merepresentasikan state pintu
    public enum DoorState
    {
        Terkunci,
        Terbuka
    }

    // Properti untuk menyimpan state saat ini
    public DoorState CurrentState { get; private set; }

    // Konstruktor dengan state-based construction (state awal: Terkunci)
    public DoorMachine()
    {
        CurrentState = DoorState.Terkunci;
        DisplayStateMessage();
    }

    // Method untuk mengubah state pintu menjadi Terkunci
    public void Lock()
    {
        CurrentState = DoorState.Terkunci;
        DisplayStateMessage();
    }

    // Method untuk mengubah state pintu menjadi Terbuka
    public void Unlock()
    {
        CurrentState = DoorState.Terbuka;
        DisplayStateMessage();
    }

    // Method untuk menampilkan pesan berdasarkan state saat ini
    private void DisplayStateMessage()
    {
        if (CurrentState == DoorState.Terkunci)
        {
            Console.WriteLine("Pintu terkunci");
        }
        else if (CurrentState == DoorState.Terbuka)
        {
            Console.WriteLine("Pintu tidak terkunci");
        }
    }
}

class Program
{
    static void Main()
    {
        // Membuat instance dari class DoorMachine
        DoorMachine door = new DoorMachine();

        // Mensimulasikan perubahan state
        door.Unlock();  // Mengubah state menjadi Terbuka
        door.Lock();    // Mengubah state menjadi Terkunci
    }
}
