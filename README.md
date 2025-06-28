# PLC_with_SIMATICS7

1 Introduction
Chapter ini memperkenalkan Programmable Logic Controller (PLC) dan fungsinya dalam mengendalikan operation machine atau plant sesuai dengan function cycle yang ditentukan.

1.1 Number system
Menjelaskan bahwa PLC menggunakan binary number system (dual number system), yang hanya terdiri dari digit 0 dan 1, untuk memproses address storage location, input, output, time, dan lain-lain. Setiap digit dalam binary number diberi value berdasarkan power 2.
1.2 Terms from computer science
Part ini menjelaskan term dasar yang sering digunakan dalam context PLC yang berasal dari computer science:
1.2.1 Bit: Unit informasi binary terkecil, dapat berupa "1" (voltage ada) atau "0" (voltage tidak ada).
1.2.2 Byte: Unit yang terdiri dari delapan bit.
1.2.3 Word: Terdiri dari dua byte atau 16 bit, digunakan untuk merepresentasikan binary number, letter, atau control instruction.
1.2.4 Bit address: Setiap bit dalam satu byte diberi address dari 0 (paling kanan) hingga 7 (paling kiri) agar system dapat mendeteksi dan mengalamatinya.
1.2.5 Byte address: Setiap byte diberi number sebagai byte address (misalnya, IB 2 untuk input byte 2 atau QB 4 untuk output byte 4). Kombinasi bit address dan byte address secara unik mengalamati bit individual.
1.2.6 Word address: Penomoran word menghasilkan word address. Saat menggunakan word (misalnya, IW, QW, MW, DW), word address selalu merupakan byte address yang lebih rendah dari dua byte terkait.
2 Arrangement of a PLC
Bab ini membahas bagaimana sebuah PLC diatur. PLC diproduksi secara massal dan pada awalnya tidak memiliki tugas spesifik. Mereka dilengkapi dengan semua component yang diperlukan untuk control engineering, seperti logic elements, latching/unlatching functions, time, counter, dll. Component ini dihubungkan melalui programming untuk membentuk controller yang berfungsi. Terdapat berbagai control unit yang berbeda berdasarkan functional unit-nya, termasuk input dan output, storage location, counter, time, bit memory functions, special functions, operating speed, dan type of program processing. Untuk control task yang besar, control unit dirakit secara modular, memungkinkan customization. Sementara itu, untuk control task yang kecil, manufacturer menawarkan compact control unit dengan fixed number input dan output.

2.1 Structure of a PLC
Menjelaskan basic structure dari programmable logic controller (PLC) yang menunjukkan interaksi antara PLC, signaling equipment, dan actuator atau indicator light.
2.2 Structure of an automation unit
Menguraikan basic structure dari automation unit yang terdiri dari central processing unit (CPU), program memory, power supply unit, bus system, dan input dan output modules. Signaling equipment memasok digital dan analog signal ke PLC, sedangkan actuator atau indicator light menerima digital dan analog signal dari PLC.
2.3 Hardware requirements
Menyebutkan hardware component yang diperlukan untuk bekerja dengan example dalam book, yaitu DIN rail, power supply unit (PS), central processing unit (CPU), input and output module, MPI cable, personal computer (PC), dan programming unit (PU).
2.3.1 Hardware structure
Menjelaskan slot rule yang harus diperhatikan saat menyiapkan S7-300. Power supply unit (PS) harus selalu menjadi module pertama di DIN rail, diikuti oleh central processing unit (CPU) sebagai module kedua. Input dan output modules dipasang setelah CPU. Maksimal delapan signal module dapat dipasang di samping CPU. Module dapat dipasang secara horizontal atau vertikal.
2.4 Software requirements
Menjelaskan software yang dibutuhkan untuk programming S7-300, yaitu Windows XP operating system dan STEP 7 software package Version 3.xx. Version ini mengintegrasikan tiga method of representation: Statement List (STL), Ladder Diagram (LAD), dan Function Block Diagram (FBD). Diasumsikan bahwa STEP 7 software package sudah terinstal dan user memiliki basic knowledge tentang Windows XP operating system (pengelolaan file).
2.4.1 STEP 7 programming language
Menjelaskan bahwa setelah penggantian SIMATIC S5 dengan SIMATIC S7 pada Autumn 1995, new programming language (STEP 7) dikembangkan berdasarkan IEC 1131 standard. Programming language ini menyediakan seluruh functionality untuk parameterizing, configuring, dan programming S7-300 automation unit. STEP 7 berjalan di bawah Windows XP dan bekerja secara object-oriented basis. Symbol untuk object dipetakan pada graphical user interface, dan STEP 7 memiliki integrated online help system.
2.4.2 Objects
Pada graphical user interface, system merepresentasikan object dengan symbol. Setiap symbol ditetapkan ke specific object. STEP 7 object menawarkan access ke processing functions seperti membuat, membuka, mengedit, menyimpan, mengganti nama, menghapus, menyalin, dan menempel object. Sebuah object dapat berisi symbol seperti project, SIMATIC station, atau S7 program.
2.4.3 Projects
STEP 7 memungkinkan division plant menjadi project. Sebuah project berisi semua data untuk automation solution dan dianggap sebagai most important object. Project structure dijelaskan dengan example elevator control.
2.4.4 Configuring an S7-300
Menjelaskan bahwa saat configuring, S7 module diatur dalam configuration table. Module dapat dipilih dari electronic catalogue dan dimasukkan ke configuration table sesuai dengan slot. Address secara otomatis ditetapkan ke setiap module.
2.4.5 Parameterization
Menjelaskan bahwa properties dari individual module dapat diatur dengan berbagai cara. Salah satu parameter adalah cycle time monitoring dengan CPU S7-300, yang parameter-nya dapat diubah.
Bab 3: Way of Functioning of a PLC (Cara Kerja PLC)

Bab ini menjelaskan bagaimana sebuah PLC beroperasi dan komponen-komponen penyusunnya.

3.1 Modules of the PLC (Modul-modul PLC)
Subbab ini menjelaskan berbagai Modules yang membentuk PLC dan interaksi antar Modules tersebut.
3.1.1 Power supply unit (Unit catu daya)
Unit ini bertanggung jawab untuk mengkonversi tegangan listrik AC (120/230 V) menjadi tegangan DC (24 V) untuk menyediakan daya bagi Modules elektronik PLC. Tegangan untuk Signalling Equipment, Actuators, dan Indicator Lights (yang di atas 24 V) disuplai oleh unit listrik atau Control-power Transformers tambahan.
3.1.2 Program memory (Memori program)
Ini adalah komponen di mana informasi disimpan dalam bentuk sinyal biner. Memory ini terdiri dari sejumlah Storage Locations. Jenis-jenis Memory yang dijelaskan meliputi:
RAM (Random-Access Memory): Memory baca-tulis yang bersifat volatil (informasi hilang saat daya mati).
ROM (Read-Only Memory): Memory baca-saja yang isinya tidak dapat dihapus atau diubah oleh pengguna.
EPROM (Erasable Programmable Read-Only Memory): Memory yang seluruh isinya dapat dihapus menggunakan sinar UV dan dapat diprogram ulang.
REPROM (Reprogrammable Erasable Read-Only Memory): Mirip dengan EPROM, isinya juga dihapus dengan sinar UV.
EEPROM (Electrically Erasable Programmable Read-Only Memory): Memungkinkan penghapusan dan penulisan setiap Storage Location secara elektrik.
EAPROM (Electrically Alterable Programmable Read-Only Memory).
3.1.3 Central processing unit (CPU)
CPU adalah "otak" PLC. Processor di dalam CPU memproses Program yang tersimpan di Memory. Ini memeriksa status Input dan kemudian menginstruksikan Output Module untuk mengaktifkan atau menonaktifkan Actuators atau Indicator Lights yang terhubung. CPU juga menangani pertukaran data dengan Peripheral melalui Peripheral Bus. Proses ini melibatkan pemindahan status Input ke Process Input Image (PII), kemudian aplikasi Timer, Counter, dan Accumulator, serta pemindahan hasil Logical Operations (RLO) ke Process Output Image (PIQ).
3.1.4 Bus system (Sistem bus)
Sistem Bus adalah jalur grup untuk mentransfer sinyal. Ini terdiri dari tiga jalur sinyal paralel:
Address bus: Digunakan untuk mengalamati Address pada Modules individu.
Data bus: Digunakan untuk mentransfer Data (misalnya, dari Input ke Output Modules).
Control bus: Digunakan untuk mentransfer sinyal untuk mengontrol dan memantau Function Cycle di dalam Programmable Controller.
3.1.5 Input and output modules (Modul input dan output)
Modules ini digunakan oleh sistem untuk bertukar data dengan proses yang akan dikontrol, yaitu menerima sinyal dari Signalling Equipment dan mengirimkan sinyal ke Actuators atau Indicator Lights.
Bab 4: Program Processing and Programming (Pemrosesan dan Pemrograman Program)

Bab ini menjelaskan bagaimana program PLC diproses dan berbagai cara untuk memprogramnya.

4.1 Linear program processing (Pemrosesan program linear)
Pemrosesan program linear umumnya digunakan untuk Controller yang sederhana dan tidak terlalu kompleks. Program diproses dalam urutan di mana Statements disimpan di Program Memory. Setelah Program End (BE) tercapai, pemrosesan dimulai kembali dari awal. Waktu yang dibutuhkan untuk memproses semua Statements satu kali disebut Cycle Time, sehingga jenis pemrosesan ini juga disebut Cyclical Processing.

4.2 Structured programming (Pemrograman terstruktur)
Untuk Control Jobs yang kompleks, Program dibagi menjadi Program Blocks yang lebih kecil dan mudah dikelola, yang diatur berdasarkan fungsi. Keuntungannya adalah Program Sections dapat diuji secara individual dan kemudian digabungkan menjadi Overall Function jika berfungsi. STEP 7 menyediakan User Blocks berikut:

Organization Block (OB): Dipanggil secara siklis oleh Operating System dan berfungsi sebagai Interface antara User Program dan Operating System. OB memberitahukan Processor tentang Program Blocks yang harus diproses.
Function Block (FB): Memiliki Memory Area yang ditetapkan. Saat FB dipanggil, Data Block (DB) dapat ditetapkan padanya, memungkinkan akses ke Data di Instance DB tersebut. FB dapat ditetapkan ke DB yang berbeda dan dapat memanggil FBs dan FCs lainnya.
Function (FC): Tidak memiliki Memory Area yang ditetapkan. Local Data dari Function hilang setelah pemrosesan Function.
Data Block (DB): Digunakan untuk menyediakan Memory untuk Data Variables. Ada Global DBs (di mana semua OBs, FBs, dan FCs dapat membaca atau menulis data) dan Instance DBs (yang ditetapkan untuk FB tertentu).
System Blocks for standard and system functions: Fungsi siap pakai yang disimpan di CPU dan dapat dipanggil oleh User. Ini termasuk System Function Block (SFB), System Function (SFC), dan System Data Block (SDB).
4.3 Control instruction (Instruksi kontrol)
Control Job dipecah menjadi individual Control Instructions untuk diproses oleh PLC. Control Instruction adalah unit independen dari Controller Program, mewakili sebuah Directive.

4.3.1 Operation part (Bagian operasi): Menjelaskan fungsi yang akan dieksekusi. Ini dibedakan menjadi Organizational Operations, Binary Operations, dan Digital Operations.
4.3.2 Examples for digital operations (Contoh operasi digital): Contoh termasuk Load (L), Transfer (T), Compare to "greater than integers" (>I), Compare to "same as real numbers" (==R), dan Subtraction with real numbers (-R).
4.3.3 Examples of binary operations (Contoh operasi biner): Contoh termasuk AND (&), NOT (N), OR (≥1), dan Assignment (=).
4.3.4 Examples of organizational operations (Contoh operasi organisasi): Contoh termasuk Block Call Conditioned (CC), Block Call Unconditioned (UC), Open Data Block (OPN), Jump Unconditional (JU), Jump Conditional (JC), Block End Unconditional (BEU), dan Block End Conditional (BEC).
4.3.5 Operand part (Bagian operand): Berisi semua informasi yang diperlukan untuk mengeksekusi Operation, menyatakan apa yang harus dieksekusi oleh Processor. Operand Identifier menunjukkan Type of Operand (misalnya, I untuk Inputs, Q untuk Outputs, M untuk Bit Memories, T untuk Times, C untuk Counters, dll.), dan Operand Parameter menunjukkan Address dari Operand.
4.4 Addressing (Pengalamatan)

4.4.1 Symbolic Addressing (Pengalamatan Simbolik): Memungkinkan penugasan nama simbolik (misalnya, END_STOP) ke Absolute Address tertentu untuk kemudahan pemahaman.
4.4.2 Absolute addressing (Pengalamatan Absolut): Pilihan pengalamatan meliputi Immediate Addressing, Direct Addressing, dan Memory-indirect Addressing.
4.4.3 Immediate addressing (Pengalamatan Langsung): Operand terkandung dalam Operation, artinya nilai yang akan dikerjakan langsung mengikuti atau tersirat.
4.4.3.1 Direct addressing (Pengalamatan Langsung): Address Operand terkandung dalam Operation, yang menunjuk langsung ke Address dari Value yang akan diproses.
4.4.3.2 Memory-indirect addressing (Pengalamatan Tidak Langsung Memori): Address Operand ditentukan secara tidak langsung melalui Operand lain yang berisi Address dari yang pertama, menggunakan Pointer. Word atau Double Word dapat berada di Bit Memory (M), Data Block (DB), Instance Data Block (DI), atau Local Data (L).
4.5 Program representation (Representasi program)
Representasi program didasarkan pada Terms of Reference yang menjelaskan fungsi yang akan diimplementasikan. Di STEP 7, program dapat direpresentasikan dan diprogram dalam tiga cara:

4.5.1 Ladder Diagram (LAD): Representasi diagram kontrol menggunakan simbol yang mirip dengan Wiring Diagram konvensional, tetapi diatur secara horizontal.
4.5.2 Function Block Diagram (FBD): Representasi diagram kontrol menggunakan simbol Logic Boxes dari Boolean Algebra, dengan Inputs di sisi kiri dan Outputs di sisi kanan.
4.5.3 Statement List (STL): Menggambarkan kontrol dengan Control Instructions individual menggunakan Mnemonic Abbreviations.
4.6 Flags (Memori Bit)
Bit Memories digunakan untuk Logic Operations dalam Controller tanpa perlu melewati sinyal di luar Controller. Ini adalah Electronic Storage Elements (RS Flip-flops) untuk menyimpan Signal Status Conditions "0" dan "1".

4.6.1 Retentive bit memories (Memori bit retentif): Mempertahankan status terakhir saat Supply Voltage dimatikan atau saat beralih dari mode operasi RUN > STOP, berkat Buffer Battery. Dapat di-reset melalui User Program.
4.6.2 Non-retentive bit memories (Memori bit non-retentif): Di-reset saat beralih dari mode operasi RUN > STOP dan saat Power On.
Bab 5: Logic Operations (Operasi Logika)

Bab ini membahas operasi logika dasar pada PLC, khususnya operasi AND, dan menyediakan langkah-langkah praktis untuk memprogram dan menguji program tersebut menggunakan PC dan Siemens SIMATIC S7-300.

5.1 Basic logic operations (Operasi logika dasar)
Subbab ini memperkenalkan konsep operasi logika AND dan contoh penggunaannya untuk mengaktifkan Indicator Light berdasarkan status dua Switches.
5.1.1 Clearing the CPU (Membersihkan CPU)
Menjelaskan prosedur untuk membersihkan CPU dari Blocks yang "lama" sebelum memulai Programming baru. Ini memastikan CPU berada dalam kondisi kosong untuk Program baru.
5.1.2 Creating projects (Membuat Project)
Langkah-langkah untuk membuat Project baru di SIMATIC Manager untuk Program operasi AND.
5.1.3 Inserting the SIMATIC 300 station (Memasukkan Stasiun SIMATIC 300)
Panduan untuk memasukkan SIMATIC 300 Station ke dalam Project yang sedang aktif.
5.1.4 Configuring and parameterizing (Mengkonfigurasi dan Memparameterisasi)
Langkah-langkah untuk mengkonfigurasi dan memparameterisasi SIMATIC Station, termasuk menambahkan Hardware Components (seperti DIN Rail) dari Hardware Catalog.
5.1.5 Arrangement of the power supply (Pengaturan Power Supply)
Prosedur untuk memasang Power Supply Unit (PS 307 2A) ke DIN Rail di Slot 1.
5.1.6 Arrangement of the CPU 314 (Pengaturan CPU 314)
Prosedur untuk memasang CPU 314 ke DIN Rail di Slot 2.
5.1.7 Arrangement of the input module (Pengaturan Modul Input)
Prosedur untuk memasang Digital Input Module (DI) dengan 16 Inputs ke DIN Rail di Slot 4 (Slot 3 dikosongkan untuk IM Module).
5.1.8 Arrangement of the output module (Pengaturan Modul Output)
Prosedur untuk memasang Digital Output Module (DO) dengan 16 Outputs ke DIN Rail di Slot 5.
5.1.9 Parameterizing the CPU 314 (Memparameterisasi CPU 314)
Langkah-langkah untuk mengatur parameter CPU 314, termasuk Scan Cycle Monitoring Time dan mengaktifkan Clock Memory.
5.1.10 Saving the global configuration (Menyimpan Konfigurasi Global)
Instruksi untuk menyimpan Konfigurasi Global yang telah dibuat ke dalam Project.
5.1.11 Transferring the configuration to the CPU (Mentransfer Konfigurasi ke CPU)
Proses mengunduh Konfigurasi yang telah disimpan ke CPU S7-300 agar pengaturan tersebut berlaku.
5.2 Logical AND operation user program (Program Pengguna Operasi AND Logika)
Bagian ini secara spesifik membahas bagaimana membuat Program Pengguna untuk operasi AND Logika.
Organization block (OB 1): Menjelaskan peran OB 1 sebagai Interface antara Operating System CPU dan User Program, serta tempat ditentukan Sequence of Processing.
A Function (FC): Mendefinisikan Function sebagai Code Block tanpa Memory yang cocok untuk Recurring Functions.
5.2.1 Entering FCs (FC 1) (Memasukkan FCs (FC 1))
Langkah-langkah untuk membuat dan memasukkan FC 1 dalam Project, serta memilih FBD sebagai Type of Representation.
5.2.2 S7 block function (Fungsi Block S7)
Penjelasan tentang penggunaan Fungsi Block S7, khususnya Function, dan cara memilih Type of Representation (FBD dalam kasus ini).
5.2.3 Entering OB 1 (Memasukkan OB 1)
Langkah-langkah untuk membuat dan memasukkan OB 1 ke dalam Project, memilih STL sebagai Type of Representation, dan menulis Control Instruction CALL FC 1.
5.2.4 Downloading (Mengunduh)
Proses mengunduh Blocks (FC 1 dan OB 1) ke CPU S7-300 untuk pengujian.
5.2.5 Testing (Pengujian)
Prosedur untuk menguji fungsionalitas User Program, termasuk membuka Block secara online dan mengatur Test Display.
5.2.6 Specifying trigger conditions (Menentukan Kondisi Trigger)
Menjelaskan cara menentukan Trigger Conditions untuk Pengujian Program, seperti memilih Test Situation (Process atau Laboratory).
5.2.7 Deactivating the FBD program status (Mendeaktivasi Status Program FBD)
Cara menonaktifkan tampilan Program Status FBD setelah Pengujian.
5.2.8 Testing with STL (Pengujian dengan STL)
Menunjukkan bagaimana Program Operasi AND Logika yang ditulis dalam FBD juga dapat diuji menggunakan Representasi STL.
5.2.9 Testing with LAD (Pengujian dengan LAD)
Menunjukkan bagaimana Program Operasi AND Logika juga dapat diuji menggunakan Representasi LAD.
5.2.10 Extending from two to three inputs (3rd. input 10.2) (Memperluas dari dua ke tiga Input (Input ke-3 10.2))
Menjelaskan cara memperluas Logic Program dari dua menjadi tiga Input.
5.2.10.1 Extending with STL (Memperluas dengan STL)
5.2.10.2 Extending with LAD (Memperluas dengan LAD)
5.2.10.3 Extending with FBD (Memperluas dengan FBD)
5.2.11 Reducing from 3 inputs to 2 (delete 10.2) (Mengurangi dari 3 Input menjadi 2 (hapus 10.2))
Menjelaskan cara mengurangi Logic Program dari tiga menjadi dua Input.
5.2.11.1 Reducing with STL (Mengurangi dengan STL)
5.2.11.2 Reducing with LAD (Mengurangi dengan LAD)
5.2.11.3 Reducing with FBD (Mengurangi dengan FBD)
5.3 Logical OR operation user program (Program Pengguna Operasi OR Logika)
Subbab ini membahas Program Pengguna untuk Operasi OR Logika.
5.3.1 Entering the program using the PC (FBD) (Memasukkan Program menggunakan PC (FBD))
5.3.2 Create the project (Membuat Project)
5.3.3 Copy SIMATIC station 1 into another project (Menyalin Stasiun SIMATIC 1 ke Project lain)
5.3.4 Change OB 1 (Mengubah OB 1)
5.3.5 Downloading (Mengunduh)
5.3.6 Testing (Pengujian)
Bab 6: Program Input (Memasukkan Program)

Bab ini membahas berbagai metode input program dan contoh-contoh praktisnya.

6.1 AND before OR (AND sebelum OR)
Subbab ini menjelaskan konsep dan implementasi operasi logika "AND sebelum OR" dalam pemrograman PLC. Ini melibatkan penggunaan kombinasi operasi AND dan OR untuk mencapai kondisi kontrol tertentu.
6.2 OR before AND (OR sebelum AND)
Subbab ini menjelaskan konsep dan implementasi operasi logika "OR sebelum AND", yang merupakan kebalikan dari "AND sebelum OR". Ini juga melibatkan kombinasi operasi OR dan AND.
6.3 Poll for signal state 0 (Polling untuk status sinyal 0)
Subbab ini membahas bagaimana PLC dapat melakukan polling atau memeriksa status sinyal 0 (OFF) sebagai bagian dari Logika Program.
6.4 Exclusive OR operation (Operasi Eksklusif OR)
Subbab ini menjelaskan operasi logika Exclusive OR (XOR) dan cara menggunakannya dalam pemrograman PLC. Operasi ini menghasilkan Output True hanya jika jumlah Input yang True adalah ganjil.
6.5 Polling outputs (Polling Output)
Subbab ini menjelaskan bagaimana PLC dapat melakukan polling atau memeriksa status Output yang ada, yang berguna untuk Program Logic yang lebih kompleks.
6.6 Inserting networks (Memasukkan Network)
Subbab ini membahas cara memasukkan Networks baru ke dalam Program PLC. Network adalah segmen Program yang berisi Logika Kontrol.
6.7 Latch circuit with the PC (Rangkaian Latch dengan PC)
Subbab ini menjelaskan cara mengimplementasikan Latch Circuit (Rangkaian Pengunci) menggunakan PC (Personal Computer) untuk mengontrol PLC. Latch Circuit memungkinkan suatu Output untuk tetap aktif setelah Input Trigger dihilangkan.
6.8 Practical examples of control with the PC (Contoh praktis kontrol dengan PC)
Subbab ini menyediakan berbagai contoh praktis mengenai aplikasi kontrol menggunakan PLC dan PC.
6.8.1 Temperature difference (Perbedaan Suhu)
Contoh ini mungkin melibatkan kontrol berdasarkan perbedaan Suhu yang terdeteksi.
6.8.2 Drinks machine (Mesin Minuman)
Contoh ini mungkin menjelaskan Logika Kontrol untuk Dispenser Minuman otomatis.
6.8.3 Intercom
Contoh ini mungkin membahas kontrol Sistem Intercom menggunakan PLC.
6.8.4 Generator
Contoh ini mungkin menjelaskan Program Kontrol untuk Generator.
6.8.5 Boiler control (Kontrol Boiler)
Contoh ini kemungkinan membahas Program Kontrol untuk Sistem Boiler.
6.8.6 Smelting furnaces (Tungku Peleburan)
Contoh ini mungkin melibatkan Kontrol Otomatisasi untuk Tungku Peleburan.
6.9 Flip-flop
Subbab ini menjelaskan konsep Flip-flop dalam PLC. Flip-flop adalah Sirkuit Elektronik yang mampu menyimpan satu Bit informasi.
6.9.1 R-S flip-flop (Flip-flop R-S)
Penjelasan mengenai R-S Flip-flop, salah satu jenis Flip-flop dasar.
6.9.2 Entering the program (Memasukkan Program)
Langkah-langkah untuk memasukkan Program yang mengimplementasikan Flip-flop.
6.9.3 Pump controller (Pengontrol Pompa)
Contoh praktis tentang bagaimana Flip-flop dapat digunakan dalam Kontrol Pompa.
Bab 7: Creating Momentary Impulses (Edge Instructions) (Membuat Impuls Sesaat (Instruksi Tepi))

Bab ini menjelaskan cara membuat Impulses sesaat atau Edge Instructions dalam PLC, yang berguna untuk mendeteksi perubahan status sinyal dari OFF ke ON (Rising Edge) atau dari ON ke OFF (Falling Edge).

7.1 Momentary impulse with a rising edge (FP) (Impuls sesaat dengan Rising Edge (FP))
Subbab ini membahas konsep Momentary Impulse yang dihasilkan oleh Rising Edge (perubahan dari 0 ke 1) dari sinyal Input. Saat sinyal Input berubah dari LOW ke HIGH, Output yang terkait akan aktif sesaat.
7.2 Momentary impulse with a falling edge (FN) (Impuls sesaat dengan Falling Edge (FN))
Subbab ini menjelaskan konsep Momentary Impulse yang dihasilkan oleh Falling Edge (perubahan dari 1 ke 0) dari sinyal Input. Saat sinyal Input berubah dari HIGH ke LOW, Output yang terkait akan aktif sesaat.
7.3 Program input (Memasukkan Program)
Subbab ini menjelaskan langkah-langkah untuk memasukkan Program yang mengimplementasikan instruksi Edge.
7.4 Acknowledgement circuit (Sirkuit Pengakuan)
Subbab ini membahas bagaimana Momentary Impulses atau Edge Instructions dapat digunakan dalam Acknowledgement Circuit, di mana suatu tindakan hanya terjadi setelah sinyal pengakuan sesaat diterima.
Bab 8: Timing Functions (Fungsi Pewaktu)

Bab ini membahas berbagai fungsi pewaktu (Timer) yang tersedia dalam PLC dan bagaimana mengimplementasikannya dalam program.

8.1 Timing value specification (Spesifikasi nilai pewaktu)
Subbab ini menjelaskan bagaimana nilai waktu (Time Value) ditentukan untuk Timer, yang biasanya merupakan kombinasi dari Time Base (misalnya, 10 ms, 100 ms, 1 s) dan Time Value (misalnya, 50 untuk 500 ms jika Time Base 10 ms).
8.2 Release a time (FR) (Melepas pewaktu (FR))
Subbab ini membahas instruksi "FR" (Freezing Time), yang digunakan untuk menghentikan atau membekukan nilai waktu pada Timer.
8.3 Current value (Nilai saat ini)
Subbab ini menjelaskan bagaimana Current Value (nilai waktu yang berjalan) dari Timer dapat diakses dan digunakan dalam Program.
8.4 Reset time (Reset pewaktu)
Subbab ini membahas bagaimana Timer dapat di-reset kembali ke nilai awal atau nol.
8.5 Selection of times (five different ones) (Pemilihan pewaktu (lima jenis berbeda))
Subbab ini merinci lima jenis Timer berbeda yang umum digunakan dalam PLC:
8.5.1 Pulse timer (SP) (Pewaktu pulsa (SP))
Timer ini menghasilkan Pulse Output dengan durasi yang ditentukan ketika Input diaktifkan. Output akan OFF setelah durasi waktu berlalu, meskipun Input masih ON.
8.5.2 Extended pulse timer (SE) (Pewaktu pulsa diperpanjang (SE))
Mirip dengan Pulse Timer, tetapi Output akan tetap ON selama durasi waktu yang ditentukan setelah Input menjadi ON, dan Output akan OFF bahkan jika Input berubah menjadi OFF sebelum durasi waktu berakhir.
8.5.3 Switch-on delay timer (SD) (Pewaktu tunda ON (SD))
Timer ini akan mengaktifkan Output setelah durasi waktu yang ditentukan berlalu, dengan syarat Input tetap ON selama durasi tersebut.
8.5.4 Retentive switch-on delay timer (SS) (Pewaktu tunda ON retentif (SS))
Mirip dengan Switch-on Delay Timer, tetapi Timer ini bersifat retentif, artinya nilai waktu yang dihitung akan tetap tersimpan meskipun terjadi pemadaman daya atau transisi mode.
8.5.5 Switch-off delay timer (SF) (Pewaktu tunda OFF (SF))
Timer ini akan menunda pemadaman Output setelah Input menjadi OFF. Output akan tetap ON selama durasi waktu yang ditentukan setelah Input OFF.
8.6 PC program input of timing functions (Memasukkan Program PC untuk Fungsi Pewaktu)
Subbab ini memberikan contoh praktis tentang bagaimana Fungsi Pewaktu dapat diimplementasikan menggunakan PC dalam pemrograman PLC.
8.6.1 Garage lighting (Penerangan Garasi)
Contoh ini mungkin menjelaskan bagaimana Timer digunakan untuk mengontrol pencahayaan garasi.
8.6.2 Filling system (Sistem Pengisian)
Contoh ini mungkin membahas bagaimana Timer digunakan dalam Sistem Pengisian (misalnya, untuk mengontrol durasi pengisian).
8.6.3 Compressor system (Sistem Kompresor)
Contoh ini mungkin menjelaskan bagaimana Timer digunakan dalam Kontrol Sistem Kompresor.
Bab 9: Clock Generators (Generator Detak)

Bab ini menjelaskan penggunaan Clock Generators dalam PLC untuk menghasilkan sinyal detak dengan frekuensi tertentu, yang sering digunakan untuk berbagai aplikasi kontrol yang memerlukan sinyal periodik.

9.1 PC program input with clock generator (Memasukkan Program PC dengan Clock Generator)
Subbab ini membahas bagaimana program PLC dapat diimplementasikan menggunakan PC untuk memanfaatkan Clock Generator yang sudah terintegrasi dalam CPU. Clock Memory diaktifkan melalui Parameterization CPU.
9.1.1 Channel switch (Sakelar Saluran)
Contoh ini kemungkinan menjelaskan bagaimana Clock Generator digunakan untuk mengontrol suatu "Channel Switch", mungkin untuk mengalihkan sinyal atau kondisi secara periodik.
9.1.2 Paging system (Sistem Panggilan)
Contoh ini mungkin membahas bagaimana Clock Generator digunakan dalam Sistem Paging (misalnya, untuk membunyikan bel atau sinyal secara berkala).
9.1.3 Air supply (Pasokan Udara)
Contoh ini kemungkinan menjelaskan bagaimana Clock Generator digunakan untuk mengontrol Pasokan Udara, mungkin dalam siklus periodik untuk suatu proses.
Bab 10: Counters (Pencacah)

Bab ini membahas penggunaan Counter dalam PLC untuk menghitung Impulse atau Event, serta berbagai fungsi yang terkait dengan Counter.

10.1 Load and transfer functions (Fungsi Load dan Transfer)
Subbab ini kemungkinan menjelaskan bagaimana nilai dapat di-Load ke Counter dan bagaimana nilai dari Counter dapat di-Transfer untuk digunakan dalam bagian lain dari Program.
10.2 Counter functions (Fungsi Counter)
Subbab ini merinci berbagai fungsi spesifik dari Counter:
10.2.1 Release a counter (FR) (Melepas Counter (FR))
Fungsi ini mungkin digunakan untuk menghentikan atau membekukan nilai pada Counter.
10.2.2 Counting forwards (Menghitung maju)
Fungsi ini mengaktifkan Counter untuk menghitung naik (menambah) setiap kali ada Impulse.
10.2.3 Counting backwards (Menghitung mundur)
Fungsi ini mengaktifkan Counter untuk menghitung turun (mengurangi) setiap kali ada Impulse.
10.2.4 Set counter (Mengatur Counter)
Fungsi ini digunakan untuk mengatur Counter ke nilai awal yang ditentukan.
10.2.5 Count value definition (Definisi nilai hitungan)
Menjelaskan bagaimana nilai hitungan target atau batas untuk Counter ditentukan.
10.2.6 Reset counter (R) (Reset Counter (R))
Fungsi ini digunakan untuk mereset nilai Counter kembali ke nol atau nilai awal yang ditentukan.
10.2.7 Poll count value (L/LC) (Polling nilai hitungan (L/LC))
Menjelaskan bagaimana nilai hitungan saat ini dari Counter dapat dibaca atau di-Poll.
10.2.8 Poll signal state of counter (binary) (Polling status sinyal Counter (biner))
Menjelaskan bagaimana status sinyal biner dari Counter (misalnya, apakah sudah mencapai nilai tertentu) dapat di-Poll.
10.3 PC program input cleaning bath (Memasukkan Program PC untuk Bak Pembersih)
Subbab ini menyediakan contoh praktis tentang bagaimana Counter dapat digunakan dalam Program PLC untuk mengontrol Proses "Cleaning Bath" atau Bak Pembersih.
Bab 11: Comparators (Komparator)

Bab ini membahas fungsi Comparators dalam PLC, yang digunakan untuk membandingkan nilai-nilai dan menghasilkan Output berdasarkan hasil perbandingan tersebut.

11.1 Comparison functions (Fungsi Perbandingan)
Subbab ini merinci berbagai jenis Comparison Functions yang tersedia:
11.1.1 Equal to == (Sama dengan ==)
Membandingkan apakah dua nilai Input sama.
11.1.2 Not equal <> (Tidak sama dengan <>)
Membandingkan apakah dua nilai Input tidak sama.
11.1.3 Greater than equal to >= (Lebih besar atau sama dengan >=)
Membandingkan apakah nilai Input pertama lebih besar atau sama dengan nilai Input kedua.
11.1.4 Greater than > (Lebih besar dari >)
Membandingkan apakah nilai Input pertama lebih besar dari nilai Input kedua.
11.1.5 Less than equal to <= (Lebih kecil atau sama dengan <=)
Membandingkan apakah nilai Input pertama lebih kecil atau sama dengan nilai Input kedua.
11.1.6 Less than < (Lebih kecil dari <)
Membandingkan apakah nilai Input pertama lebih kecil dari nilai Input kedua.
11.2 PC program input runway light (Memasukkan Program PC untuk Lampu Landasan Pacu)
Subbab ini menyediakan contoh praktis tentang bagaimana Comparators dapat digunakan dalam Program PLC untuk mengontrol "Runway Light" (Lampu Landasan Pacu).
11.3 Program input sequence function (Memasukkan Program Fungsi Urutan)
Subbab ini menjelaskan bagaimana Comparators dapat digunakan dalam Programming untuk mengimplementasikan "Sequence Function" atau fungsi urutan, di mana suatu tindakan terjadi berdasarkan urutan atau tahapan nilai tertentu.
Bab 12: Practical Examples with Simulators (Contoh Praktis dengan Simulator)

Bab ini menyajikan berbagai contoh praktis aplikasi PLC yang dapat diuji menggunakan Simulator.

12.1 Seven-segment display (Layar Tujuh-segmen)
Contoh ini kemungkinan membahas bagaimana PLC diprogram untuk mengontrol Seven-segment Display, yang digunakan untuk menampilkan angka atau karakter.
12.2 Star-delta starting (Pengaktifan Bintang-delta)
Contoh ini menjelaskan bagaimana PLC digunakan untuk mengontrol Star-delta Starting pada Motor Listrik, yang merupakan metode untuk mengurangi arus awal saat Motor dihidupkan.
12.3 Traffic light controller (Pengontrol Lampu Lalu Lintas)
Contoh ini membahas Program PLC untuk mengontrol Sistem Lampu Lalu Lintas.
12.4 Conveyor belt controller (Pengontrol Konveyor)
Contoh ini menjelaskan bagaimana PLC digunakan untuk mengontrol Gerakan dan Operasi Conveyor Belt.
12.5 Reaction vessel (Bejana Reaksi)
Contoh ini mungkin melibatkan Kontrol Otomatisasi untuk Bejana Reaksi dalam Proses Kimia atau Industri.
12.6 Container filling system (Sistem Pengisian Kontainer)
Contoh ini membahas Program PLC untuk Sistem Pengisian Kontainer otomatis.
12.7 Automatic tablet filler (Pengisi Tablet Otomatis)
Contoh ini kemungkinan menjelaskan Program PLC untuk Pengisi Tablet Otomatis di Industri Farmasi atau sejenisnya.
12.8 Door access control system (Sistem Kontrol Akses Pintu)
Contoh ini membahas bagaimana PLC dapat digunakan dalam Sistem Kontrol Akses Pintu.
12.9 Pump controller (Pengontrol Pompa)
Contoh ini kemungkinan menjelaskan lebih lanjut tentang Program Kontrol untuk Pompa, mungkin dengan berbagai skenario dan kondisi.
Bab 13: Sequence Control Systems (Sistem Kontrol Sekuen)

Bab ini memperkenalkan konsep Sistem Kontrol Sekuen, yang digunakan untuk mengontrol proses yang berjalan melalui serangkaian langkah atau tahapan.

13.1 Introduction (Pendahuluan)
Subbab ini memberikan pengantar umum tentang apa itu Sequence Control System dan mengapa itu penting dalam Otomasi.
13.2 Components of a sequence control system (Komponen Sistem Kontrol Sekuen)
Subbab ini menjelaskan komponen-komponen yang membentuk sebuah Sequence Control System.
13.3 Type of representation (Jenis representasi)
Subbab ini kemungkinan membahas berbagai cara untuk merepresentasikan Sequence Control System, seperti menggunakan Diagram Keadaan atau Flowchart.
13.4 Linear sequence cascade (Kaskade Sekuen Linear)
Subbab ini menjelaskan Kaskade Sekuen Linear, di mana setiap langkah dalam sekuen harus diselesaikan sebelum langkah berikutnya dapat dimulai.
13.5 Sheet metal bending device (Perangkat Pembengkok Lembaran Logam)
Subbab ini menyediakan contoh praktis tentang bagaimana Sequence Control System diterapkan pada Perangkat Pembengkok Lembaran Logam.
Bab 14: Safety Regulations (Peraturan Keselamatan)

Bab ini membahas pentingnya peraturan keselamatan dalam pengoperasian PLC dan sistem otomatisasi.

14.1 Rules (Aturan)
Subbab ini kemungkinan menguraikan berbagai Aturan Keselamatan umum yang harus dipatuhi.
14.2 Emergency STOP control release (Pelepas Kontrol Emergency STOP)
Subbab ini menjelaskan fungsi dan pentingnya Emergency STOP Control Release, yang dirancang untuk menghentikan Operasi Mesin atau Sistem secara cepat dalam keadaan darurat.
14.3 Example of a control release (Contoh Pelepas Kontrol)
Subbab ini memberikan Contoh praktis tentang bagaimana Sistem Control Release diimplementasikan.
