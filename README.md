<!DOCTYPE html>
<html>

<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Aplikasi Gudang Penyimpanan Ade</title>

  <style>
    body {

            font-family: 'Inter', sans-serif;

            background-color: #f0f2f5;

            display: flex;

            min-height: 100vh;

        }

        @keyframes fade-in-down {

            from { opacity: 0; transform: translateY(-20px); }

            to { opacity: 1; transform: translateY(0); }

        }

        @keyframes fade-out-up {

            from { opacity: 1; transform: translateY(0); }

            to { opacity: 0; transform: translateY(-20px); }

        }

        .animate-fade-in-down {

            animation: fade-in-down 0.3s ease-out forwards;

        }

        .animate-fade-out-up {

            animation: fade-out-up 0.3s ease-in forwards;

        }

        @media (max-width: 768px) {

            .sidebar {

                width: 100%;

                position: relative;

                height: auto;

                box-shadow: none;

                padding-bottom: 0;

            }

            .main-content {

                margin-left: 0;

                padding-top: 1rem;

            }

        }

        .tab-button.active {

            background-color: #3b82f6;

            color: white;

            font-weight: 600;

        }

        .single-item-input-grid {

            display: grid;

            grid-template-columns: repeat(1, 1fr);

            gap: 1rem;

        }

        @media (min-width: 640px) {

            .single-item-input-grid {

                grid-template-columns: repeat(2, 1fr);

            }

        }

        @media (min-width: 1024px) {

            .single-item-input-grid {

                grid-template-columns: repeat(3, 1fr);

            }

        }
  </style>

  
</head>
<body>
  <script src="https://cdn.tailwindcss.com"></script>

    





    <div class="sidebar w-64 bg-gray-800 text-white p-6 fixed h-full overflow-y-auto shadow-xl z-10 md:block hidden">

        <h2 class="text-2xl font-bold mb-6 text-center">Menu Gudang</h2>

        <nav>

            <ul>

                <li class="mb-4">

                    <a href="#" id="nav-dashboard" class="block p-3 rounded-lg hover:bg-gray-700 transition duration-200 text-lg">Dashboard</a>

                </li>

                <li class="mb-4">

                    <a href="#" id="nav-manajemen-item" class="block p-3 rounded-lg hover:bg-gray-700 transition duration-200 text-lg active-nav">Manajemen Item</a>

                </li>

                <li class="mb-4">

                    <span class="block p-3 text-lg font-semibold text-gray-400">Transaksi Barang</span>

                    <ul class="ml-4 mt-2 space-y-2">

                        <li>

                            <a href="#" id="nav-transaksi-eksternal" class="block p-2 rounded-lg hover:bg-gray-700 transition duration-200 text-base">Transaksi Eksternal</a>

                        </li>

                        <li>

                            <a href="#" id="nav-transaksi-internal" class="block p-2 rounded-lg hover:bg-gray-700 transition duration-200 text-base">Transaksi Internal</a>

                        </li>

                    </ul>

                </li>

                <li class="mb-4">

                    <a href="#" id="nav-pihak-terkait" class="block p-3 rounded-lg hover:bg-gray-700 transition duration-200 text-lg">Pihak Terkait</a>

                </li>

                <li class="mb-4">

                    <a href="#" id="nav-backup-restore" class="block p-3 rounded-lg hover:bg-gray-700 transition duration-200 text-lg">Backup & Restore Data</a>

                </li>

                <li class="mb-4">

                    <a href="#" id="nav-laporan" class="block p-3 rounded-lg hover:bg-gray-700 transition duration-200 text-lg">Laporan</a>

                </li>

                <li class="mb-4">

                    <a href="#" id="nav-pengaturan" class="block p-3 rounded-lg hover:bg-gray-700 transition duration-200 text-lg">Pengaturan</a>

                </li>

            </ul>

        </nav>

    </div>



    <div class="main-content flex-grow md:ml-64 p-4">

        <div id="section-manajemen-item" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto">

            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Manajemen Item</h1>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mb-6">

                <div>

                    <label for="itemCategoryInput" class="block text-sm font-medium text-gray-700 mb-1">Kategori Barang:</label>

                    <input type="text" id="itemCategoryInput" placeholder="Contoh: Elektronik" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700"/>

                </div>

                <div>

                    <label for="itemNameInput" class="block text-sm font-medium text-gray-700 mb-1">Nama Barang:</label>

                    <input type="text" id="itemNameInput" placeholder="Contoh: Laptop" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700"/>

                </div>

                <div>

                    <label for="itemSpecSizeInput" class="block text-sm font-medium text-gray-700 mb-1">Spec/Size:</label>

                    <input type="text" id="itemSpecSizeInput" placeholder="Contoh: 15 inci, 8GB RAM" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700"/>

                </div>

                <div>

                    <label for="itemUnitInput" class="block text-sm font-medium text-gray-700 mb-1">Unit:</label>

                    <input type="text" id="itemUnitInput" placeholder="Contoh: Pcs, Box" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700"/>

                </div>

            </div>

            <div class="flex flex-col sm:flex-row gap-3 mb-8">

                <button id="saveItemBtn" class="flex-grow bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tambah Item</button>

                <button id="cancelEditBtn" class="flex-grow bg-gray-400 hover:bg-gray-500 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 hidden">Batal Edit</button>

            </div>

            <h2 class="text-2xl font-bold text-gray-800 mb-4">Daftar Item Gudang:</h2>

            <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                <table class="min-w-full divide-y divide-gray-200">

                    <thead class="bg-gray-100">

                        <tr>

                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Kategori Barang</th>

                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>

                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Spec/Size</th>

                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Unit</th>

                            <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                        </tr>

                    </thead>

                    <tbody id="itemsTableBody" class="bg-white divide-y divide-gray-200">

                    </tbody>

                </table>

            </div>

            <button id="clearAllItemsBtn" class="w-full mt-8 bg-red-500 hover:bg-red-600 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Hapus Semua Item</button>

        </div>



        <div id="section-transaksi-eksternal" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto hidden">

            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Transaksi Eksternal</h1>

            <div class="flex border-b border-gray-200 mb-6">

                <button data-tab="penerimaan" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent active">Penerimaan</button>

                <button data-tab="pembelian" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Pembelian</button>

                <button data-tab="pengiriman" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Pengiriman</button>

                <button data-tab="transaksi-lain-eksternal" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Transaksi Lain</button>

            </div>



            <div id="tab-penerimaan" class="tab-content">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Penerimaan Barang</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="receiptDate" class="block text-sm font-medium text-gray-700 mb-1">Tanggal:</label>

                        <input type="date" id="receiptDate" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="receiptDocNum" class="block text-sm font-medium text-gray-700 mb-1">Nomor Dokumen:</label>

                        <input type="text" id="receiptDocNum" placeholder="Masukkan nomor dokumen" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="receiptSiteName" class="block text-sm font-medium text-gray-700 mb-1">Nama Site:</label>

                        <select id="receiptSiteName" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Site</option>

                        </select>

                    </div>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Tambah Detail Barang:</h4>

                <div class="space-y-4 border p-4 rounded-lg bg-gray-50 mb-6">

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Nama Barang:</label>

                        <select id="currentReceiptItemNameSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Barang</option>

                        </select>

                    </div>

                    <div class="single-item-input-grid">

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Brand:</label>

                            <input type="text" id="currentReceiptItemBrandInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Brand">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Kode Barang:</label>

                            <input type="text" id="currentReceiptItemCodeInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Kode Barang">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Serial Number:</label>

                            <input type="text" id="currentReceiptItemSerialInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Serial Number">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Nomor Asset:</label>

                            <input type="text" id="currentReceiptItemAssetInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Nomor Asset">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Qty:</label>

                            <input type="number" min="1" id="currentReceiptItemQtyInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Jumlah">

                        </div>

                    </div>

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Keterangan:</label>

                        <textarea id="currentReceiptItemNotesInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" rows="2" placeholder="Keterangan tambahan"></textarea>

                    </div>

                    <button id="addCurrentReceiptItemToListBtn" class="bg-indigo-500 hover:bg-indigo-600 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tambah ke Daftar</button>

                    <button id="cancelEditCurrentReceiptItemBtn" class="bg-gray-400 hover:bg-gray-500 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 hidden">Batal Edit Item</button>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Daftar Barang dalam Penerimaan ini:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm mb-6">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Brand</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Qty</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Keterangan</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="currentReceiptItemsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

                <button id="saveReceiptBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan Penerimaan</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar Penerimaan yang Tersimpan:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Tanggal</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">No. Dokumen</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Site</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jumlah Item</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="receiptsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>



            <div id="tab-pembelian" class="tab-content hidden">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Pembelian Barang</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="purchaseDate" class="block text-sm font-medium text-gray-700 mb-1">Tanggal:</label>

                        <input type="date" id="purchaseDate" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="purchaseDocNum" class="block text-sm font-medium text-gray-700 mb-1">Nomor Dokumen:</label>

                        <input type="text" id="purchaseDocNum" placeholder="Masukkan nomor dokumen" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="purchaseSupplierNameSelect" class="block text-sm font-medium text-gray-700 mb-1">Nama Supplier:</label>

                        <select id="purchaseSupplierNameSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Supplier</option>

                        </select>

                    </div>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Tambah Detail Barang:</h4>

                <div class="space-y-4 border p-4 rounded-lg bg-gray-50 mb-6">

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Nama Barang:</label>

                        <select id="currentPurchaseItemNameSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Barang</option>

                        </select>

                    </div>

                    <div class="single-item-input-grid">

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Brand:</label>

                            <input type="text" id="currentPurchaseItemBrandInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Brand">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Kode Barang:</label>

                            <input type="text" id="currentPurchaseItemCodeInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Kode Barang">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Serial Number:</label>

                            <input type="text" id="currentPurchaseItemSerialInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Serial Number">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Nomor Asset:</label>

                            <input type="text" id="currentPurchaseItemAssetInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Nomor Asset">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Qty:</label>

                            <input type="number" min="1" id="currentPurchaseItemQtyInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Jumlah">

                        </div>

                    </div>

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Keterangan:</label>

                        <textarea id="currentPurchaseItemNotesInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" rows="2" placeholder="Keterangan tambahan"></textarea>

                    </div>

                    <button id="addCurrentPurchaseItemToListBtn" class="bg-indigo-500 hover:bg-indigo-600 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tambah ke Daftar</button>

                    <button id="cancelEditCurrentPurchaseItemBtn" class="bg-gray-400 hover:bg-gray-500 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 hidden">Batal Edit Item</button>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Daftar Barang dalam Pembelian ini:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm mb-6">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Brand</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Qty</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Keterangan</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="currentPurchaseItemsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

                <button id="savePurchaseBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan Pembelian</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar Pembelian yang Tersimpan:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Tanggal</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">No. Dokumen</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Supplier</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jumlah Item</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="purchasesTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>



            <div id="tab-pengiriman" class="tab-content hidden">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Pengiriman Barang</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="shipmentDate" class="block text-sm font-medium text-gray-700 mb-1">Tanggal:</label>

                        <input type="date" id="shipmentDate" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="shipmentDocNum" class="block text-sm font-medium text-gray-700 mb-1">Nomor Dokumen:</label>

                        <input type="text" id="shipmentDocNum" placeholder="Masukkan nomor dokumen" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="shipmentDestinationSiteSelect" class="block text-sm font-medium text-gray-700 mb-1">Nama Site Tujuan:</label>

                        <select id="shipmentDestinationSiteSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Site Tujuan</option>

                        </select>

                    </div>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Tambah Detail Barang:</h4>

                <div class="space-y-4 border p-4 rounded-lg bg-gray-50 mb-6">

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Nama Barang:</label>

                        <select id="currentShipmentItemNameSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Barang</option>

                        </select>

                    </div>

                    <div class="single-item-input-grid">

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Brand:</label>

                            <input type="text" id="currentShipmentItemBrandInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Brand">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Kode Barang:</label>

                            <input type="text" id="currentShipmentItemCodeInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Kode Barang">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Serial Number:</label>

                            <input type="text" id="currentShipmentItemSerialInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Serial Number">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Nomor Asset:</label>

                            <input type="text" id="currentShipmentItemAssetInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Nomor Asset">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Qty:</label>

                            <input type="number" min="1" id="currentShipmentItemQtyInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Jumlah">

                        </div>

                    </div>

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Keterangan:</label>

                        <textarea id="currentShipmentItemNotesInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" rows="2" placeholder="Keterangan tambahan"></textarea>

                    </div>

                    <button id="addCurrentShipmentItemToListBtn" class="bg-indigo-500 hover:bg-indigo-600 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tambah ke Daftar</button>

                    <button id="cancelEditCurrentShipmentItemBtn" class="bg-gray-400 hover:bg-gray-500 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 hidden">Batal Edit Item</button>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Daftar Barang dalam Pengiriman ini:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm mb-6">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Brand</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Qty</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Keterangan</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="currentShipmentItemsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

                <button id="saveShipmentBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan Pengiriman</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar Pengiriman yang Tersimpan:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Tanggal</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">No. Dokumen</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Site Tujuan</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jumlah Item</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="shipmentsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>



            <div id="tab-transaksi-lain-eksternal" class="tab-content hidden">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Transaksi Eksternal Lain</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="otherExternalDate" class="block text-sm font-medium text-gray-700 mb-1">Tanggal:</label>

                        <input type="date" id="otherExternalDate" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="otherExternalDocNum" class="block text-sm font-medium text-gray-700 mb-1">Nomor Dokumen:</label>

                        <input type="text" id="otherExternalDocNum" placeholder="Masukkan nomor dokumen" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="otherExternalPartyName" class="block text-sm font-medium text-gray-700 mb-1">Nama Pihak Terkait:</label>

                        <input type="text" id="otherExternalPartyName" placeholder="Nama pihak terkait" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="otherExternalTransactionTypeSelect" class="block text-sm font-medium text-gray-700 mb-1">Jenis Transaksi:</label>

                        <select id="otherExternalTransactionTypeSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Jenis Transaksi</option>

                            <option value="kerusakan">Kerusakan</option>

                            <option value="kehilangan">Kehilangan</option>

                            <option value="lain-lain">Lain-lain</option>

                        </select>

                    </div>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Tambah Detail Barang:</h4>

                <div class="space-y-4 border p-4 rounded-lg bg-gray-50 mb-6">

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Nama Barang:</label>

                        <select id="currentOtherExternalItemNameSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Barang</option>

                        </select>

                    </div>

                    <div class="single-item-input-grid">

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Brand:</label>

                            <input type="text" id="currentOtherExternalItemBrandInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Brand">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Kode Barang:</label>

                            <input type="text" id="currentOtherExternalItemCodeInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Kode Barang">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Serial Number:</label>

                            <input type="text" id="currentOtherExternalItemSerialInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Serial Number">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Nomor Asset:</label>

                            <input type="text" id="currentOtherExternalItemAssetInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Nomor Asset">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Qty:</label>

                            <input type="number" min="1" id="currentOtherExternalItemQtyInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Jumlah">

                        </div>

                    </div>

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Keterangan:</label>

                        <textarea id="currentOtherExternalItemNotesInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" rows="2" placeholder="Keterangan tambahan"></textarea>

                    </div>

                    <button id="addCurrentOtherExternalItemToListBtn" class="bg-indigo-500 hover:bg-indigo-600 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tambah ke Daftar</button>

                    <button id="cancelEditCurrentOtherExternalItemBtn" class="bg-gray-400 hover:bg-gray-500 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 hidden">Batal Edit Item</button>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Daftar Barang dalam Transaksi ini:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm mb-6">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Brand</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Qty</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Keterangan</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="currentOtherExternalItemsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

                <button id="saveOtherExternalTransactionBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan Transaksi Lain</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar Transaksi Lain Eksternal yang Tersimpan:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Tanggal</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">No. Dokumen</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pihak Terkait</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jenis Transaksi</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jumlah Item</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="otherExternalTransactionsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>

        </div>



        <div id="section-transaksi-internal" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto hidden">

            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Transaksi Internal</h1>

            <div class="flex border-b border-gray-200 mb-6">

                <button data-tab="peminjaman" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent active">Peminjaman</button>

                <button data-tab="pengembalian" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Pengembalian</button>

                <button data-tab="transaksi-lain-internal" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Transaksi Lain</button>

            </div>



            <div id="tab-peminjaman" class="tab-content">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Peminjaman Barang</h3>

                <p class="text-gray-600">Di sini akan ada form untuk mencatat peminjaman barang antar departemen atau pihak internal.</p>

                <div class="mt-4 p-4 border border-dashed border-gray-300 rounded-lg text-gray-500">

                    Form input dan tabel peminjaman akan diletakkan di sini.

                </div>

            </div>

            <div id="tab-pengembalian" class="tab-content hidden">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Pengembalian Barang</h3>

                <p class="text-gray-600">Di sini akan ada form untuk mencatat pengembalian barang.</p>

                <div class="mt-4 p-4 border border-dashed border-gray-300 rounded-lg text-gray-500">

                    Form input dan tabel pengembalian akan diletakkan di sini.

                </div>

            </div>

            <div id="tab-transaksi-lain-internal" class="tab-content hidden">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Transaksi Internal Lain</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="otherInternalDate" class="block text-sm font-medium text-gray-700 mb-1">Tanggal:</label>

                        <input type="date" id="otherInternalDate" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="otherInternalDocNum" class="block text-sm font-medium text-gray-700 mb-1">Nomor Dokumen:</label>

                        <input type="text" id="otherInternalDocNum" placeholder="Masukkan nomor dokumen" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="otherInternalPartyName" class="block text-sm font-medium text-gray-700 mb-1">Nama Pihak Terkait:</label>

                        <input type="text" id="otherInternalPartyName" placeholder="Nama pihak terkait (misal: Departemen IT)" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="otherInternalTransactionTypeSelect" class="block text-sm font-medium text-gray-700 mb-1">Jenis Transaksi:</label>

                        <select id="otherInternalTransactionTypeSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Jenis Transaksi</option>

                            <option value="kerusakan">Kerusakan</option>

                            <option value="kehilangan">Kehilangan</option>

                            <option value="lain-lain">Lain-lain</option>

                        </select>

                    </div>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Tambah Detail Barang:</h4>

                <div class="space-y-4 border p-4 rounded-lg bg-gray-50 mb-6">

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Nama Barang:</label>

                        <select id="currentOtherInternalItemNameSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                            <option value="">Pilih Barang</option>

                        </select>

                    </div>

                    <div class="single-item-input-grid">

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Brand:</label>

                            <input type="text" id="currentOtherInternalItemBrandInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Brand">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Kode Barang:</label>

                            <input type="text" id="currentOtherInternalItemCodeInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Kode Barang">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Serial Number:</label>

                            <input type="text" id="currentOtherInternalItemSerialInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Serial Number">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Nomor Asset:</label>

                            <input type="text" id="currentOtherInternalItemAssetInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Nomor Asset">

                        </div>

                        <div>

                            <label class="block text-sm font-medium text-gray-700 mb-1">Qty:</label>

                            <input type="number" min="1" id="currentOtherInternalItemQtyInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" placeholder="Jumlah">

                        </div>

                    </div>

                    <div class="col-span-full">

                        <label class="block text-sm font-medium text-gray-700 mb-1">Keterangan:</label>

                        <textarea id="currentOtherInternalItemNotesInput" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700" rows="2" placeholder="Keterangan tambahan"></textarea>

                    </div>

                    <button id="addCurrentOtherInternalItemToListBtn" class="bg-indigo-500 hover:bg-indigo-600 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tambah ke Daftar</button>

                    <button id="cancelEditCurrentOtherInternalItemBtn" class="bg-gray-400 hover:bg-gray-500 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 hidden">Batal Edit Item</button>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Daftar Barang dalam Transaksi ini:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm mb-6">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Brand</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Qty</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Keterangan</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="currentOtherInternalItemsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

                <button id="saveOtherInternalTransactionBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan Transaksi Lain</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar Transaksi Lain Internal yang Tersimpan:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Tanggal</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">No. Dokumen</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pihak Terkait</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jenis Transaksi</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Jumlah Item</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="otherInternalTransactionsTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>

        </div>



        <div id="section-pihak-terkait" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto hidden">

            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Pihak Terkait</h1>

            <div class="flex border-b border-gray-200 mb-6">

                <button data-tab="supplier" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent active">Supplier</button>

                <button data-tab="user" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">User</button>

                <button data-tab="site" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Site</button>

            </div>



            <div id="tab-supplier" class="tab-content">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Data Supplier</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="supplierNameInput" class="block text-sm font-medium text-gray-700 mb-1">Nama Supplier:</label>

                        <input type="text" id="supplierNameInput" placeholder="Nama Supplier" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="supplierContactInput" class="block text-sm font-medium text-gray-700 mb-1">Nomor Kontak:</label>

                        <input type="text" id="supplierContactInput" placeholder="Nomor Kontak" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="supplierAddressInput" class="block text-sm font-medium text-gray-700 mb-1">Alamat:</label>

                        <textarea id="supplierAddressInput" placeholder="Alamat Supplier" rows="3" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700"></textarea>

                    </div>

                </div>

                <button id="saveSupplierBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan Supplier</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar Supplier:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Supplier</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nomor Kontak</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Alamat</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="suppliersTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>



            <div id="tab-user" class="tab-content hidden">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Data User</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="userNameInput" class="block text-sm font-medium text-gray-700 mb-1">Nama User:</label>

                        <input type="text" id="userNameInput" placeholder="Nama User" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="userSectionInput" class="block text-sm font-medium text-gray-700 mb-1">Section:</label>

                        <input type="text" id="userSectionInput" placeholder="Section (misal: IT, HRD)" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="userStatusInput" class="block text-sm font-medium text-gray-700 mb-1">Status:</label>

                        <input type="text" id="userStatusInput" placeholder="Status (misal: Aktif, Non-aktif)" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                </div>



                <h4 class="text-xl font-bold text-gray-700 mb-3">Nama Anggota:</h4>

                <div id="memberNamesContainer" class="space-y-2 border p-4 rounded-lg bg-gray-50 mb-6">

                </div>

                <button id="addMemberNameBtn" class="bg-indigo-500 hover:bg-indigo-600 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 mb-6">Tambah Anggota</button>

                <button id="saveUserBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan User</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar User:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama User</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Section</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Anggota</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="usersTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>



            <div id="tab-site" class="tab-content hidden">

                <h3 class="text-2xl font-bold text-gray-700 mb-4">Form Data Site</h3>

                <div class="space-y-4 mb-6">

                    <div>

                        <label for="siteNameInput" class="block text-sm font-medium text-gray-700 mb-1">Nama Site:</label>

                        <input type="text" id="siteNameInput" placeholder="Nama Site" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="sitePICInput" class="block text-sm font-medium text-gray-700 mb-1">PIC:</label>

                        <input type="text" id="sitePICInput" placeholder="Person In Charge" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    </div>

                    <div>

                        <label for="siteAddressInput" class="block text-sm font-medium text-gray-700 mb-1">Alamat:</label>

                        <textarea id="siteAddressInput" placeholder="Alamat Site" rows="3" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700"></textarea>

                    </div>

                </div>

                <button id="saveSiteBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-5 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105 w-full">Simpan Site</button>



                <h4 class="text-xl font-bold text-gray-700 mt-8 mb-3">Daftar Site:</h4>

                <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">

                    <table class="min-w-full divide-y divide-gray-200">

                        <thead class="bg-gray-100">

                            <tr>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Site</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">PIC</th>

                                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Alamat</th>

                                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">Aksi</th>

                            </tr>

                        </thead>

                        <tbody id="sitesTableBody" class="bg-white divide-y divide-gray-200">

                        </tbody>

                    </table>

                </div>

            </div>

        </div>



        <div id="section-backup-restore" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto hidden">

            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Backup & Restore Data</h1>

            <div class="space-y-6">

                <p class="text-gray-700">Di sini Anda dapat melakukan backup data aplikasi Anda ke file lokal atau mengembalikan data dari file backup yang ada.</p>



                <div class="border p-4 rounded-lg bg-gray-50">

                    <h3 class="text-xl font-bold text-gray-700 mb-3">Backup Data</h3>

                    <p class="mb-4 text-gray-600">Ekspor semua data gudang Anda (Item, Transaksi, Supplier, User, Site) ke file JSON.</p>

                    <button id="backupDataBtn" class="bg-green-600 hover:bg-green-700 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Ekspor Data</button>

                </div>



                <div class="border p-4 rounded-lg bg-gray-50">

                    <h3 class="text-xl font-bold text-gray-700 mb-3">Restore Data</h3>

                    <p class="mb-4 text-gray-600">Impor data dari file JSON. <strong>PERINGATAN: Ini akan menimpa data yang ada!</strong></p>

                    <input type="file" id="restoreFileInput" accept=".json" class="block w-full text-sm text-gray-500 file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-blue-50 file:text-blue-700 hover:file:bg-blue-100 mb-4"/>

                    <button id="restoreDataBtn" class="bg-red-600 hover:bg-red-700 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Impor Data</button>

                </div>

            </div>

        </div>



        <div id="section-dashboard" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto hidden">

            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Dashboard</h1>

            <p class="text-gray-600">Area untuk ringkasan dan statistik gudang.</p>

        </div>

        <div id="section-laporan" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto hidden">
            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Laporan</h1>

            <div class="flex border-b border-gray-200 mb-6">
                <button data-tab="global-report" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent active">Global</button>
                <button data-tab="user-report" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Per User</button>
                <button data-tab="site-report" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Per Site</button>
                <button data-tab="supplier-report" class="tab-button py-2 px-4 text-lg text-gray-600 hover:text-blue-600 hover:border-blue-600 border-b-2 border-transparent">Per Supplier</button>
            </div>

            <div id="tab-global-report" class="tab-content">
                <h3 class="text-2xl font-bold text-gray-700 mb-4">Laporan Global</h3>
                <p class="text-gray-600">Ringkasan statistik dan jumlah total barang dari semua data yang tersimpan.</p>
                <div class="mt-4 p-4 border border-dashed border-gray-300 rounded-lg text-gray-500">
                    Data laporan global akan muncul di sini (misal: jumlah total item, total transaksi).
                </div>
                </div>

            <div id="tab-user-report" class="tab-content hidden">
                <h3 class="text-2xl font-bold text-gray-700 mb-4">Laporan Per User</h3>
                <p class="text-gray-600">Detail aktivitas barang yang terkait dengan masing-masing user/departemen.</p>
                 <div class="space-y-4 mb-6">
                    <div>
                        <label for="reportUserSelect" class="block text-sm font-medium text-gray-700 mb-1">Pilih User:</label>
                        <select id="reportUserSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">
                            <option value="">Pilih User</option>
                        </select>
                    </div>
                    <button id="generateUserReportBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tampilkan Laporan</button>
                </div>
                <div id="userReportOutput" class="mt-4 p-4 border border-dashed border-gray-300 rounded-lg text-gray-500">
                    Laporan detail per user akan muncul di sini.
                </div>
            </div>

            <div id="tab-site-report" class="tab-content hidden">
                <h3 class="text-2xl font-bold text-gray-700 mb-4">Laporan Per Site</h3>
                <p class="text-gray-600">Ringkasan barang yang berada di setiap lokasi/site.</p>
                 <div class="space-y-4 mb-6">
                    <div>
                        <label for="reportSiteSelect" class="block text-sm font-medium text-gray-700 mb-1">Pilih Site:</label>
                        <select id="reportSiteSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">
                            <option value="">Pilih Site</option>
                        </select>
                    </div>
                    <button id="generateSiteReportBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tampilkan Laporan</button>
                </div>
                <div id="siteReportOutput" class="mt-4 p-4 border border-dashed border-gray-300 rounded-lg text-gray-500">
                    Laporan detail per site akan muncul di sini.
                </div>
            </div>

            <div id="tab-supplier-report" class="tab-content hidden">
                <h3 class="text-2xl font-bold text-gray-700 mb-4">Laporan Per Supplier</h3>
                <p class="text-gray-600">Daftar barang yang diterima/dibeli dari setiap supplier.</p>
                <div class="space-y-4 mb-6">
                    <div>
                        <label for="reportSupplierSelect" class="block text-sm font-medium text-gray-700 mb-1">Pilih Supplier:</label>
                        <select id="reportSupplierSelect" class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">
                            <option value="">Pilih Supplier</option>
                        </select>
                    </div>
                    <button id="generateSupplierReportBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded-lg shadow-md transition duration-300 ease-in-out transform hover:scale-105">Tampilkan Laporan</button>
                </div>
                <div id="supplierReportOutput" class="mt-4 p-4 border border-dashed border-gray-300 rounded-lg text-gray-500">
                    Laporan detail per supplier akan muncul di sini.
                </div>
            </div>
        </div>

        <div id="section-pengaturan" class="content-section bg-white p-8 rounded-xl shadow-lg w-full max-w-4xl mx-auto hidden">

            <h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Pengaturan</h1>

            <p class="text-gray-600">Area untuk konfigurasi aplikasi.</p>

        </div>



    </div>

  <script>
    document.addEventListener('DOMContentLoaded', () => {

            const itemCategoryInput = document.getElementById('itemCategoryInput');

            const itemNameInput = document.getElementById('itemNameInput');

            const itemSpecSizeInput = document.getElementById('itemSpecSizeInput');

            const itemUnitInput = document.getElementById('itemUnitInput');

            const saveItemBtn = document.getElementById('saveItemBtn');

            const cancelEditBtn = document.getElementById('cancelEditBtn');

            const itemsTableBody = document.getElementById('itemsTableBody');

            const clearAllItemsBtn = document.getElementById('clearAllItemsBtn');



            const receiptDateInput = document.getElementById('receiptDate');

            const receiptDocNumInput = document.getElementById('receiptDocNum');

            const receiptSiteNameSelect = document.getElementById('receiptSiteName');

            const currentReceiptItemNameSelect = document.getElementById('currentReceiptItemNameSelect');

            const currentReceiptItemBrandInput = document.getElementById('currentReceiptItemBrandInput');

            const currentReceiptItemCodeInput = document.getElementById('currentReceiptItemCodeInput');

            const currentReceiptItemSerialInput = document.getElementById('currentReceiptItemSerialInput');

            const currentReceiptItemAssetInput = document.getElementById('currentReceiptItemAssetInput');

            const currentReceiptItemQtyInput = document.getElementById('currentReceiptItemQtyInput');

            const currentReceiptItemNotesInput = document.getElementById('currentReceiptItemNotesInput');

            const addCurrentReceiptItemToListBtn = document.getElementById('addCurrentReceiptItemToListBtn');

            const cancelEditCurrentReceiptItemBtn = document.getElementById('cancelEditCurrentReceiptItemBtn');

            const currentReceiptItemsTableBody = document.getElementById('currentReceiptItemsTableBody');

            const saveReceiptBtn = document.getElementById('saveReceiptBtn');

            const receiptsTableBody = document.getElementById('receiptsTableBody');

            let currentReceiptItems = [];

            let editingCurrentReceiptItemIndex = null;



            const purchaseDateInput = document.getElementById('purchaseDate');

            const purchaseDocNumInput = document.getElementById('purchaseDocNum');

            const purchaseSupplierNameSelect = document.getElementById('purchaseSupplierNameSelect');

            const currentPurchaseItemNameSelect = document.getElementById('currentPurchaseItemNameSelect');

            const currentPurchaseItemBrandInput = document.getElementById('currentPurchaseItemBrandInput');

            const currentPurchaseItemCodeInput = document.getElementById('currentPurchaseItemCodeInput');

            const currentPurchaseItemSerialInput = document.getElementById('currentPurchaseItemSerialInput');

            const currentPurchaseItemAssetInput = document.getElementById('currentPurchaseItemAssetInput');

            const currentPurchaseItemQtyInput = document.getElementById('currentPurchaseItemQtyInput');

            const currentPurchaseItemNotesInput = document.getElementById('currentPurchaseItemNotesInput');

            const addCurrentPurchaseItemToListBtn = document.getElementById('addCurrentPurchaseItemToListBtn');

            const cancelEditCurrentPurchaseItemBtn = document.getElementById('cancelEditCurrentPurchaseItemBtn');

            const currentPurchaseItemsTableBody = document.getElementById('currentPurchaseItemsTableBody');

            const savePurchaseBtn = document.getElementById('savePurchaseBtn');

            const purchasesTableBody = document.getElementById('purchasesTableBody');

            let currentPurchaseItems = [];

            let editingCurrentPurchaseItemIndex = null;



            const shipmentDateInput = document.getElementById('shipmentDate');

            const shipmentDocNumInput = document.getElementById('shipmentDocNum');

            const shipmentDestinationSiteSelect = document.getElementById('shipmentDestinationSiteSelect');

            const currentShipmentItemNameSelect = document.getElementById('currentShipmentItemNameSelect');

            const currentShipmentItemBrandInput = document.getElementById('currentShipmentItemBrandInput');

            const currentShipmentItemCodeInput = document.getElementById('currentShipmentItemCodeInput');

            const currentShipmentItemSerialInput = document.getElementById('currentShipmentItemSerialInput');

            const currentShipmentItemAssetInput = document.getElementById('currentShipmentItemAssetInput');

            const currentShipmentItemQtyInput = document.getElementById('currentShipmentItemQtyInput');

            const currentShipmentItemNotesInput = document.getElementById('currentShipmentItemNotesInput');

            const addCurrentShipmentItemToListBtn = document.getElementById('addCurrentShipmentItemToListBtn');

            const cancelEditCurrentShipmentItemBtn = document.getElementById('cancelEditCurrentShipmentItemBtn');

            const currentShipmentItemsTableBody = document.getElementById('currentShipmentItemsTableBody');

            const saveShipmentBtn = document.getElementById('saveShipmentBtn');

            const shipmentsTableBody = document.getElementById('shipmentsTableBody');

            let currentShipmentItems = [];

            let editingCurrentShipmentItemIndex = null;



            const otherExternalDateInput = document.getElementById('otherExternalDate');

            const otherExternalDocNumInput = document.getElementById('otherExternalDocNum');

            const otherExternalPartyNameInput = document.getElementById('otherExternalPartyName');

            const otherExternalTransactionTypeSelect = document.getElementById('otherExternalTransactionTypeSelect');

            const currentOtherExternalItemNameSelect = document.getElementById('currentOtherExternalItemNameSelect');

            const currentOtherExternalItemBrandInput = document.getElementById('currentOtherExternalItemBrandInput');

            const currentOtherExternalItemCodeInput = document.getElementById('currentOtherExternalItemCodeInput');

            const currentOtherExternalItemSerialInput = document.getElementById('currentOtherExternalItemSerialInput');

            const currentOtherExternalItemAssetInput = document.getElementById('currentOtherExternalItemAssetInput');

            const currentOtherExternalItemQtyInput = document.getElementById('currentOtherExternalItemQtyInput');

            const currentOtherExternalItemNotesInput = document.getElementById('currentOtherExternalItemNotesInput');

            const addCurrentOtherExternalItemToListBtn = document.getElementById('addCurrentOtherExternalItemToListBtn');

            const cancelEditCurrentOtherExternalItemBtn = document.getElementById('cancelEditCurrentOtherExternalItemBtn');

            const currentOtherExternalItemsTableBody = document.getElementById('currentOtherExternalItemsTableBody');

            const saveOtherExternalTransactionBtn = document.getElementById('saveOtherExternalTransactionBtn');

            const otherExternalTransactionsTableBody = document.getElementById('otherExternalTransactionsTableBody');

            let currentOtherExternalItems = [];

            let editingCurrentOtherExternalItemIndex = null;



            const otherInternalDateInput = document.getElementById('otherInternalDate');

            const otherInternalDocNumInput = document.getElementById('otherInternalDocNum');

            const otherInternalPartyNameInput = document.getElementById('otherInternalPartyName');

            const otherInternalTransactionTypeSelect = document.getElementById('otherInternalTransactionTypeSelect');

            const currentOtherInternalItemNameSelect = document.getElementById('currentOtherInternalItemNameSelect');

            const currentOtherInternalItemBrandInput = document.getElementById('currentOtherInternalItemBrandInput');

            const currentOtherInternalItemCodeInput = document.getElementById('currentOtherInternalItemCodeInput');

            const currentOtherInternalItemSerialInput = document.getElementById('currentOtherInternalItemSerialInput');

            const currentOtherInternalItemAssetInput = document.getElementById('currentOtherInternalItemAssetInput');

            const currentOtherInternalItemQtyInput = document.getElementById('currentOtherInternalItemQtyInput');

            const currentOtherInternalItemNotesInput = document.getElementById('currentOtherInternalItemNotesInput');

            const addCurrentOtherInternalItemToListBtn = document.getElementById('addCurrentOtherInternalItemToListBtn');

            const cancelEditCurrentOtherInternalItemBtn = document.getElementById('cancelEditCurrentOtherInternalItemBtn');

            const currentOtherInternalItemsTableBody = document.getElementById('currentOtherInternalItemsTableBody');

            const saveOtherInternalTransactionBtn = document.getElementById('saveOtherInternalTransactionBtn');

            const otherInternalTransactionsTableBody = document.getElementById('otherInternalTransactionsTableBody');

            let currentOtherInternalItems = [];

            let editingCurrentOtherInternalItemIndex = null;



            const supplierNameInput = document.getElementById('supplierNameInput');

            const supplierContactInput = document.getElementById('supplierContactInput');

            const supplierAddressInput = document.getElementById('supplierAddressInput');

            const saveSupplierBtn = document.getElementById('saveSupplierBtn');

            const suppliersTableBody = document.getElementById('suppliersTableBody');

            let editingSupplierId = null;



            const userNameInput = document.getElementById('userNameInput');

            const userSectionInput = document.getElementById('userSectionInput');

            const userStatusInput = document.getElementById('userStatusInput');

            const memberNamesContainer = document.getElementById('memberNamesContainer');

            const addMemberNameBtn = document.getElementById('addMemberNameBtn');

            const saveUserBtn = document.getElementById('saveUserBtn');

            const usersTableBody = document.getElementById('usersTableBody');

            let editingUserId = null;



            const siteNameInput = document.getElementById('siteNameInput');

            const sitePICInput = document.getElementById('sitePICInput');

            const siteAddressInput = document.getElementById('siteAddressInput');

            const saveSiteBtn = document.getElementById('saveSiteBtn');

            const sitesTableBody = document.getElementById('sitesTableBody');

            let editingSiteId = null;



            const navManajemenItem = document.getElementById('nav-manajemen-item');

            const navTransaksiEksternal = document.getElementById('nav-transaksi-eksternal');

            const navTransaksiInternal = document.getElementById('nav-transaksi-internal');

            const navPihakTerkait = document.getElementById('nav-pihak-terkait');

            const navBackupRestore = document.getElementById('nav-backup-restore');

            const navDashboard = document.getElementById('nav-dashboard');

            const navLaporan = document.getElementById('nav-laporan');

            const navPengaturan = document.getElementById('nav-pengaturan');



            const sectionManajemenItem = document.getElementById('section-manajemen-item');

            const sectionTransaksiEksternal = document.getElementById('section-transaksi-eksternal');

            const sectionTransaksiInternal = document.getElementById('section-transaksi-internal');

            const sectionPihakTerkait = document.getElementById('section-pihak-terkait');

            const sectionBackupRestore = document.getElementById('section-backup-restore');

            const sectionDashboard = document.getElementById('section-dashboard');

            const sectionLaporan = document.getElementById('section-laporan');

            const sectionPengaturan = document.getElementById('section-pengaturan');



            const backupDataBtn = document.getElementById('backupDataBtn');

            const restoreFileInput = document.getElementById('restoreFileInput');

            const restoreDataBtn = document.getElementById('restoreDataBtn');



            let db;

            const DB_NAME = 'WarehouseDB';

            const DB_VERSION = 5;

            const STORE_INVENTORY_ITEMS = 'inventoryItems';

            const STORE_EXTERNAL_RECEIPTS = 'externalReceipts';

            const STORE_EXTERNAL_PURCHASES = 'externalPurchases';

            const STORE_EXTERNAL_SHIPMENTS = 'externalShipments';

            const STORE_OTHER_EXTERNAL_TRANSACTIONS = 'otherExternalTransactions';

            const STORE_OTHER_INTERNAL_TRANSACTIONS = 'otherInternalTransactions';

            const STORE_SUPPLIERS = 'suppliers';

            const STORE_USERS = 'users';

            const STORE_SITES = 'sites';

// ... (variabel yang sudah ada)

            // Variabel untuk Laporan
            const reportUserSelect = document.getElementById('reportUserSelect');
            const generateUserReportBtn = document.getElementById('generateUserReportBtn');
            const userReportOutput = document.getElementById('userReportOutput');

            const reportSiteSelect = document.getElementById('reportSiteSelect');
            const generateSiteReportBtn = document.getElementById('generateSiteReportBtn');
            const siteReportOutput = document.getElementById('siteReportOutput');

            const reportSupplierSelect = document.getElementById('reportSupplierSelect');
            const generateSupplierReportBtn = document.getElementById('generateSupplierReportBtn');
            const supplierReportOutput = document.getElementById('supplierReportOutput');

            // ... (lanjutkan variabel lain di bawahnya)

            let editingItemId = null;



            function openDatabase() {

                return new Promise((resolve, reject) => {

                    const request = indexedDB.open(DB_NAME, DB_VERSION);

                    request.onerror = (event) => {

                        console.error('Gagal membuka IndexedDB:', event.target.errorCode);

                        showMessageBox('Error: Gagal membuka database.');

                        reject('Gagal membuka IndexedDB');

                    };

                    request.onsuccess = (event) => {

                        db = event.target.result;

                        console.log('IndexedDB berhasil dibuka.');

                        resolve(db);

                        displayItems();

                        displayReceipts();

                        displayPurchases();

                        displayShipments();

                        displayOtherExternalTransactions();

                        displayOtherInternalTransactions();

                        displaySuppliers();

                        displayUsers();

                        displaySites();

                    };

                    request.onupgradeneeded = (event) => {

                        db = event.target.result;

                        if (!db.objectStoreNames.contains(STORE_INVENTORY_ITEMS)) {

                            const objectStore = db.createObjectStore(STORE_INVENTORY_ITEMS, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('itemName', 'itemName', { unique: false });

                            console.log(`Object Store '${STORE_INVENTORY_ITEMS}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_EXTERNAL_RECEIPTS)) {

                            const objectStore = db.createObjectStore(STORE_EXTERNAL_RECEIPTS, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('receiptDate', 'receiptDate', { unique: false });

                            console.log(`Object Store '${STORE_EXTERNAL_RECEIPTS}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_EXTERNAL_PURCHASES)) {

                            const objectStore = db.createObjectStore(STORE_EXTERNAL_PURCHASES, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('purchaseDate', 'purchaseDate', { unique: false });

                            console.log(`Object Store '${STORE_EXTERNAL_PURCHASES}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_EXTERNAL_SHIPMENTS)) {

                            const objectStore = db.createObjectStore(STORE_EXTERNAL_SHIPMENTS, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('shipmentDate', 'shipmentDate', { unique: false });

                            console.log(`Object Store '${STORE_EXTERNAL_SHIPMENTS}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_OTHER_EXTERNAL_TRANSACTIONS)) {

                            const objectStore = db.createObjectStore(STORE_OTHER_EXTERNAL_TRANSACTIONS, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('otherExternalDate', 'otherExternalDate', { unique: false });

                            console.log(`Object Store '${STORE_OTHER_EXTERNAL_TRANSACTIONS}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_OTHER_INTERNAL_TRANSACTIONS)) {

                            const objectStore = db.createObjectStore(STORE_OTHER_INTERNAL_TRANSACTIONS, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('otherInternalDate', 'otherInternalDate', { unique: false });

                            console.log(`Object Store '${STORE_OTHER_INTERNAL_TRANSACTIONS}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_SUPPLIERS)) {

                            const objectStore = db.createObjectStore(STORE_SUPPLIERS, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('supplierName', 'supplierName', { unique: true });

                            console.log(`Object Store '${STORE_SUPPLIERS}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_USERS)) {

                            const objectStore = db.createObjectStore(STORE_USERS, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('userName', 'userName', { unique: true });

                            console.log(`Object Store '${STORE_USERS}' dibuat.`);

                        }

                        if (!db.objectStoreNames.contains(STORE_SITES)) {

                            const objectStore = db.createObjectStore(STORE_SITES, { keyPath: 'id', autoIncrement: true });

                            objectStore.createIndex('siteName', 'siteName', { unique: true });

                            console.log(`Object Store '${STORE_SITES}' dibuat.`);

                        }

                    };

                });

            }



            function addItem(category, name, specSize, unit) {

                if (!category.trim() || !name.trim() || !specSize.trim() || !unit.trim()) {

                    showMessageBox('Semua kolom harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_INVENTORY_ITEMS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_INVENTORY_ITEMS);

                const newItem = {

                    itemCategory: category.trim(),

                    itemName: name.trim(),

                    itemSpecSize: specSize.trim(),

                    itemUnit: unit.trim(),

                    timestamp: new Date().getTime()

                };

                const request = objectStore.add(newItem);

                request.onsuccess = () => {

                    console.log('Item berhasil disimpan.');

                    clearInputFields();

                    displayItems();

                    showMessageBox('Item berhasil ditambahkan!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan item:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan item.');

                };

            }



            function updateItem(id, category, name, specSize, unit) {

                if (!category.trim() || !name.trim() || !specSize.trim() || !unit.trim()) {

                    showMessageBox('Semua kolom harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_INVENTORY_ITEMS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_INVENTORY_ITEMS);

                const getRequest = objectStore.get(id);

                getRequest.onsuccess = (event) => {

                    const item = event.target.result;

                    if (item) {

                        item.itemCategory = category.trim();

                        item.itemName = name.trim();

                        item.itemSpecSize = specSize.trim();

                        item.itemUnit = unit.trim();

                        item.timestamp = new Date().getTime();

                        const updateRequest = objectStore.put(item);

                        updateRequest.onsuccess = () => {

                            console.log(`Item dengan ID ${id} berhasil diperbarui.`);

                            clearInputFields();

                            displayItems();

                            resetFormForAdd();

                            showMessageBox('Item berhasil diperbarui!');

                        };

                        updateRequest.onerror = (event) => {

                            console.error('Gagal memperbarui item:', event.target.errorCode);

                            showMessageBox('Error: Gagal memperbarui item.');

                        };

                    } else {

                        console.warn(`Item dengan ID ${id} tidak ditemukan untuk diperbarui.`);

                        showMessageBox('Error: Item tidak ditemukan.');

                    }

                };

                getRequest.onerror = (event) => {

                    console.error('Gagal mendapatkan item untuk diperbarui:', event.target.errorCode);

                    showMessageBox('Error: Gagal mengambil item untuk diperbarui.');

                };

            }



            function displayItems() {

                itemsTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_INVENTORY_ITEMS], 'readonly');

                const objectStore = transaction.objectStore(STORE_INVENTORY_ITEMS);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const item = cursor.value;

                        const row = itemsTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.itemCategory}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.itemName}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.itemSpecSize}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.itemUnit}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${item.id}" class="edit-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                                <button data-id="${item.id}" class="delete-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.edit-btn').addEventListener('click', () => populateFormForEdit(item.id));

                        row.querySelector('.delete-btn').addEventListener('click', () => deleteItem(item.id));

                        cursor.continue();

                    } else {

                        console.log('Semua item telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan item:', event.target.errorCode);

                    showMessageBox('Error: Gagal menampilkan item.');

                };

            }



            function populateFormForEdit(id) {

                const transaction = db.transaction([STORE_INVENTORY_ITEMS], 'readonly');

                const objectStore = transaction.objectStore(STORE_INVENTORY_ITEMS);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const item = event.target.result;

                    if (item) {

                        itemCategoryInput.value = item.itemCategory;

                        itemNameInput.value = item.itemName;

                        itemSpecSizeInput.value = item.itemSpecSize;

                        itemUnitInput.value = item.itemUnit;

                        editingItemId = item.id;

                        saveItemBtn.textContent = 'Perbarui Item';

                        saveItemBtn.classList.remove('bg-blue-600', 'hover:bg-blue-700');

                        saveItemBtn.classList.add('bg-green-600', 'hover:bg-green-700');

                        cancelEditBtn.classList.remove('hidden');

                        showMessageBox('Mode Edit: Isi form untuk memperbarui.');

                    } else {

                        showMessageBox('Item tidak ditemukan untuk diedit.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal mengambil item untuk edit:', event.target.errorCode);

                    showMessageBox('Error: Gagal mengambil item untuk diedit.');

                };

            }



            function resetFormForAdd() {

                clearInputFields();

                editingItemId = null;

                saveItemBtn.textContent = 'Tambah Item';

                saveItemBtn.classList.remove('bg-green-600', 'hover:bg-green-700');

                saveItemBtn.classList.add('bg-blue-600', 'hover:bg-blue-700');

                cancelEditBtn.classList.add('hidden');

            }

function loadAvailableSuppliers() {
                return new Promise((resolve, reject) => {
                    const transaction = db.transaction([STORE_SUPPLIERS], 'readonly');
                    const objectStore = transaction.objectStore(STORE_SUPPLIERS);
                    const request = objectStore.getAll();

                    request.onsuccess = (event) => {
                        availableSuppliers = event.target.result.map(supplier => supplier.supplierName); // Pastikan ini ada
                        availableSuppliers = [...new Set(availableSuppliers)].sort(); // Pastikan ini ada

                        // === Tambahkan ini di dalam loadAvailableSuppliers() ===
                        purchaseSupplierNameSelect.innerHTML = '<option value="">Pilih Supplier</option>' +
                            availableSuppliers.map(name => `<option value="${name}">${name}</option>`).join('');
                        reportSupplierSelect.innerHTML = '<option value="">Pilih Supplier</option>' + // Tambahkan ini
                            availableSuppliers.map(name => `<option value="${name}">${name}</option>`).join('');
                        // =================================================

                        resolve();
                    };
                    request.onerror = (event) => {
                        console.error('Gagal memuat daftar supplier:', event.target.errorCode);
                        reject();
                    };
                });
            }

            function deleteItem(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus item ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_INVENTORY_ITEMS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_INVENTORY_ITEMS);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Item dengan ID ${id} berhasil dihapus.`);

                    displayItems();

                    showMessageBox('Item berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus item:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus item.');

                };

            }
function loadAvailableSites() {
                return new Promise((resolve, reject) => {
                    const transaction = db.transaction([STORE_SITES], 'readonly');
                    const objectStore = transaction.objectStore(STORE_SITES);
                    const request = objectStore.getAll();

                    request.onsuccess = (event) => {
                        availableSites = event.target.result.map(site => site.siteName); // Pastikan ini ada
                        availableSites = [...new Set(availableSites)].sort(); // Pastikan ini ada

                        // === Tambahkan ini di dalam loadAvailableSites() ===
                        receiptSiteNameSelect.innerHTML = '<option value="">Pilih Site</option>' +
                            availableSites.map(name => `<option value="${name}">${name}</option>`).join('');
                        shipmentDestinationSiteSelect.innerHTML = '<option value="">Pilih Site Tujuan</option>' +
                            availableSites.map(name => `<option value="${name}">${name}</option>`).join('');
                        reportSiteSelect.innerHTML = '<option value="">Pilih Site</option>' + // Tambahkan ini
                            availableSites.map(name => `<option value="${name}">${name}</option>`).join('');
                        // =================================================

                        resolve();
                    };
                    request.onerror = (event) => {
                        console.error('Gagal memuat daftar site:', event.target.errorCode);
                        reject();
                    };
                });
            }


            function clearAllItems() {

                if (!confirm('Apakah kamu yakin ingin menghapus semua item?')) {

                    return;

                }

                const transaction = db.transaction([STORE_INVENTORY_ITEMS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_INVENTORY_ITEMS);

                const request = objectStore.clear();

                request.onsuccess = () => {

                    console.log('Semua item berhasil dihapus.');

                    displayItems();

                    showMessageBox('Semua item berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus semua item:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus semua item.');

                };

            }



            function clearInputFields() {

                itemCategoryInput.value = '';

                itemNameInput.value = '';

                itemSpecSizeInput.value = '';

                itemUnitInput.value = '';

            }

function loadAvailableUsers() {
                return new Promise((resolve, reject) => {
                    const transaction = db.transaction([STORE_USERS], 'readonly');
                    const objectStore = transaction.objectStore(STORE_USERS);
                    const request = objectStore.getAll();

                    request.onsuccess = (event) => {
                        availableUsers = event.target.result.map(user => user.userName); // Pastikan ini ada
                        availableUsers = [...new Set(availableUsers)].sort(); // Pastikan ini ada

                        // === Tambahkan ini di dalam loadAvailableUsers() ===
                        reportUserSelect.innerHTML = '<option value="">Pilih User</option>' +
                            availableUsers.map(name => `<option value="${name}">${name}</option>`).join('');
                        // =================================================

                        resolve();
                    };
                    request.onerror = (event) => {
                        console.error('Gagal memuat daftar user:', event.target.errorCode);
                        reject();
                    };
                });
            }

            function showMessageBox(message) {

                const messageDiv = document.createElement('div');

                messageDiv.innerHTML = message;

                messageDiv.className = 'fixed top-4 left-1/2 -translate-x-1/2 bg-blue-500 text-white p-3 rounded-lg shadow-lg z-50 animate-fade-in-down';

                document.body.appendChild(messageDiv);

                setTimeout(() => {

                    messageDiv.classList.add('animate-fade-out-up');

                    messageDiv.addEventListener('animationend', () => messageDiv.remove());

                }, 3000);

            }



            const contentSections = document.querySelectorAll('.content-section');

            const navLinks = document.querySelectorAll('nav a');



            function showSection(sectionId) {

                contentSections.forEach(section => {

                    section.classList.add('hidden');

                });

                document.getElementById(sectionId).classList.remove('hidden');



                navLinks.forEach(link => {

                    link.classList.remove('active-nav');

                });

                const activeNavLink = document.getElementById(`nav-${sectionId.replace('section-', '')}`);

                if (activeNavLink) {

                    activeNavLink.classList.add('active-nav');

                }

            }



            function setupTabs(sectionId) {

                const section = document.getElementById(sectionId);

                const tabButtons = section.querySelectorAll('.tab-button');

                const tabContents = section.querySelectorAll('.tab-content');



                tabButtons.forEach(button => {

                    button.addEventListener('click', () => {

                        tabButtons.forEach(btn => btn.classList.remove('active'));

                        tabContents.forEach(content => content.classList.add('hidden'));



                        button.classList.add('active');

                        const targetTabId = `tab-${button.dataset.tab}`;

                        document.getElementById(targetTabId).classList.remove('hidden');



                        if (sectionId === 'section-pihak-terkait' && button.dataset.tab === 'user') {

                            if (memberNamesContainer.children.length === 0) {

                                addMemberNameHandler();

                            }

                        }

                    });

                });

            }



            let availableItems = [];

            let availableSuppliers = [];

            let availableSites = [];



            function loadAvailableItems() {

                return new Promise((resolve, reject) => {

                    const transaction = db.transaction([STORE_INVENTORY_ITEMS], 'readonly');

                    const objectStore = transaction.objectStore(STORE_INVENTORY_ITEMS);

                    const request = objectStore.getAll();



                    request.onsuccess = (event) => {

                        availableItems = event.target.result;



                        currentReceiptItemNameSelect.innerHTML = '<option value="">Pilih Barang</option>' +

                            availableItems.map(item => `<option value="${item.itemName}" data-spec="${item.itemSpecSize}">${item.itemName} (${item.itemSpecSize || '-'})</option>`).join('');

                        currentPurchaseItemNameSelect.innerHTML = '<option value="">Pilih Barang</option>' +

                            availableItems.map(item => `<option value="${item.itemName}" data-spec="${item.itemSpecSize}">${item.itemName} (${item.itemSpecSize || '-'})</option>`).join('');

                        currentShipmentItemNameSelect.innerHTML = '<option value="">Pilih Barang</option>' +

                            availableItems.map(item => `<option value="${item.itemName}" data-brand="${item.brand || '-'}" data-code="${item.itemCode || '-'}" data-serial="${item.serialNumber || '-'}" data-asset="${item.assetNumber || '-'}">${item.itemName} (Brand: ${item.brand || '-'}, Kode: ${item.itemCode || '-'}, SN: ${item.serialNumber || '-'}, Asset: ${item.assetNumber || '-'})</option>`).join('');

                        currentOtherExternalItemNameSelect.innerHTML = '<option value="">Pilih Barang</option>' +

                            availableItems.map(item => `<option value="${item.itemName}" data-brand="${item.brand || '-'}" data-code="${item.itemCode || '-'}" data-serial="${item.serialNumber || '-'}" data-asset="${item.assetNumber || '-'}">${item.itemName} (Brand: ${item.brand || '-'}, Kode: ${item.itemCode || '-'}, SN: ${item.serialNumber || '-'}, Asset: ${item.assetNumber || '-'})</option>`).join('');

                        currentOtherInternalItemNameSelect.innerHTML = '<option value="">Pilih Barang</option>' +

                            availableItems.map(item => `<option value="${item.itemName}" data-brand="${item.brand || '-'}" data-code="${item.itemCode || '-'}" data-serial="${item.serialNumber || '-'}" data-asset="${item.assetNumber || '-'}">${item.itemName} (Brand: ${item.brand || '-'}, Kode: ${item.itemCode || '-'}, SN: ${item.serialNumber || '-'}, Asset: ${item.assetNumber || '-'})</option>`).join('');

                        resolve();

                    };

                    request.onerror = (event) => {

                        console.error('Gagal memuat daftar barang:', event.target.errorCode);

                        reject();

                    };

                });

            }



            function loadAvailableSuppliers() {

                return new Promise((resolve, reject) => {

                    const transaction = db.transaction([STORE_SUPPLIERS], 'readonly');

                    const objectStore = transaction.objectStore(STORE_SUPPLIERS);

                    const request = objectStore.getAll();



                    request.onsuccess = (event) => {

                        availableSuppliers = event.target.result.map(supplier => supplier.supplierName);

                        availableSuppliers = [...new Set(availableSuppliers)].sort();



                        purchaseSupplierNameSelect.innerHTML = '<option value="">Pilih Supplier</option>' +

                            availableSuppliers.map(name => `<option value="${name}">${name}</option>`).join('');

                        resolve();

                    };

                    request.onerror = (event) => {

                        console.error('Gagal memuat daftar supplier:', event.target.errorCode);

                        reject();

                    };

                });

            }



            function loadAvailableSites() {

                return new Promise((resolve, reject) => {

                    const transaction = db.transaction([STORE_SITES], 'readonly');

                    const objectStore = transaction.objectStore(STORE_SITES);

                    const request = objectStore.getAll();



                    request.onsuccess = (event) => {

                        availableSites = event.target.result.map(site => site.siteName);

                        availableSites = [...new Set(availableSites)].sort();



                        receiptSiteNameSelect.innerHTML = '<option value="">Pilih Site</option>' +

                            availableSites.map(name => `<option value="${name}">${name}</option>`).join('');

                        shipmentDestinationSiteSelect.innerHTML = '<option value="">Pilih Site Tujuan</option>' +

                            availableSites.map(name => `<option value="${name}">${name}</option>`).join('');

                        resolve();

                    };

                    request.onerror = (event) => {

                        console.error('Gagal memuat daftar site:', event.target.errorCode);

                        reject();

                    };

                });

            }

// ... (kode setupTabs lainnya)
            setupTabs('section-laporan'); // Tambahkan baris ini
            // ... (lanjutkan kode)

            function addCurrentReceiptItemToList() {

                const itemName = currentReceiptItemNameSelect.value.trim();

                const brand = currentReceiptItemBrandInput.value.trim();

                const itemCode = currentReceiptItemCodeInput.value.trim();

                const serialNumber = currentReceiptItemSerialInput.value.trim();

                const assetNumber = currentReceiptItemAssetInput.value.trim();

                const quantity = parseInt(currentReceiptItemQtyInput.value);

                const notes = currentReceiptItemNotesInput.value.trim();



                if (!itemName || isNaN(quantity) || quantity <= 0) {

                    showMessageBox('Nama Barang dan Qty (harus > 0) harus diisi untuk item!');

                    return;

                }



                const newItem = {

                    itemName, brand, itemCode, serialNumber, assetNumber, quantity, notes

                };



                if (editingCurrentReceiptItemIndex !== null) {

                    currentReceiptItems[editingCurrentReceiptItemIndex] = newItem;

                    editingCurrentReceiptItemIndex = null;

                    addCurrentReceiptItemToListBtn.textContent = 'Tambah ke Daftar';

                    cancelEditCurrentReceiptItemBtn.classList.add('hidden');

                    showMessageBox('Item berhasil diperbarui di daftar!');

                } else {

                    currentReceiptItems.push(newItem);

                    showMessageBox('Item berhasil ditambahkan ke daftar!');

                }

                clearCurrentReceiptItemInputs();

                displayCurrentReceiptItems();

            }



            function displayCurrentReceiptItems() {

                currentReceiptItemsTableBody.innerHTML = '';

                currentReceiptItems.forEach((item, index) => {

                    const row = currentReceiptItemsTableBody.insertRow();

                    row.className = 'hover:bg-gray-50';

                    row.innerHTML = `

                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.itemName}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.brand || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.quantity}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.notes || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                            <button data-index="${index}" class="edit-current-item-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                            <button data-index="${index}" class="delete-current-item-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                        </td>

                    `;

                    row.querySelector('.edit-current-item-btn').addEventListener('click', () => editCurrentReceiptItem(index));

                    row.querySelector('.delete-current-item-btn').addEventListener('click', () => deleteCurrentReceiptItem(index));

                });

            }



            function editCurrentReceiptItem(index) {

                const itemToEdit = currentReceiptItems[index];

                currentReceiptItemNameSelect.value = itemToEdit.itemName;

                currentReceiptItemBrandInput.value = itemToEdit.brand;

                currentReceiptItemCodeInput.value = itemToEdit.itemCode;

                currentReceiptItemSerialInput.value = itemToEdit.serialNumber;

                currentReceiptItemAssetInput.value = itemToEdit.assetNumber;

                currentReceiptItemQtyInput.value = itemToEdit.quantity;

                currentReceiptItemNotesInput.value = itemToEdit.notes;

                editingCurrentReceiptItemIndex = index;

                addCurrentReceiptItemToListBtn.textContent = 'Perbarui Item';

                cancelEditCurrentReceiptItemBtn.classList.remove('hidden');

                showMessageBox('Mode Edit Item: Ubah detail di atas dan klik Perbarui Item.');

            }



            function deleteCurrentReceiptItem(index) {

                if (confirm('Apakah kamu yakin ingin menghapus item ini dari daftar?')) {

                    currentReceiptItems.splice(index, 1);

                    displayCurrentReceiptItems();

                    showMessageBox('Item berhasil dihapus dari daftar!');

                }

            }



            function clearCurrentReceiptItemInputs() {

                currentReceiptItemNameSelect.value = '';

                currentReceiptItemBrandInput.value = '';

                currentReceiptItemCodeInput.value = '';

                currentReceiptItemSerialInput.value = '';

                currentReceiptItemAssetInput.value = '';

                currentReceiptItemQtyInput.value = '';

                currentReceiptItemNotesInput.value = '';

            }



            function saveReceiptTransaction() {

                const date = receiptDateInput.value;

                const docNum = receiptDocNumInput.value.trim();

                const siteName = receiptSiteNameSelect.value.trim();



                if (!date || !docNum || !siteName) {

                    showMessageBox('Tanggal, Nomor Dokumen, dan Nama Site harus diisi!');

                    return;

                }

                if (currentReceiptItems.length === 0) {

                    showMessageBox('Setidaknya harus ada satu barang yang diterima!');

                    return;

                }

                const transaction = db.transaction([STORE_EXTERNAL_RECEIPTS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_RECEIPTS);

                const newReceipt = {

                    receiptDate: date, documentNumber: docNum, siteName: siteName, items: currentReceiptItems, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newReceipt);

                request.onsuccess = () => {

                    console.log('Transaksi penerimaan berhasil disimpan.');

                    clearReceiptForm();

                    displayReceipts();

                    showMessageBox('Penerimaan berhasil dicatat!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan transaksi penerimaan:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan transaksi penerimaan.');

                };

            }



            function clearReceiptForm() {

                receiptDateInput.value = '';

                receiptDocNumInput.value = '';

                receiptSiteNameSelect.value = '';

                currentReceiptItems = [];

                editingCurrentReceiptItemIndex = null;

                clearCurrentReceiptItemInputs();

                displayCurrentReceiptItems();

                addCurrentReceiptItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentReceiptItemBtn.classList.add('hidden');

            }



            function displayReceipts() {

                receiptsTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_EXTERNAL_RECEIPTS], 'readonly');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_RECEIPTS);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const receipt = cursor.value;

                        const row = receiptsTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${receipt.receiptDate}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${receipt.documentNumber}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${receipt.siteName || '-'}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${receipt.items.length}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${receipt.id}" class="view-receipt-btn bg-blue-400 hover:bg-blue-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Lihat Detail</button>

                                <button data-id="${receipt.id}" class="delete-receipt-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.view-receipt-btn').addEventListener('click', () => viewReceiptDetail(receipt.id));

                        row.querySelector('.delete-receipt-btn').addEventListener('click', () => deleteReceipt(receipt.id));

                        cursor.continue();

                    } else {

                        console.log('Semua penerimaan telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan penerimaan:', event.target.errorCode);

                };

            }



            function viewReceiptDetail(id) {

                const transaction = db.transaction([STORE_EXTERNAL_RECEIPTS], 'readonly');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_RECEIPTS);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const receipt = event.target.result;

                    if (receipt) {

                        let detailMessage = `

                            <h4 class="font-bold text-lg mb-2">Detail Penerimaan #${receipt.id}</h4>

                            <p><strong>Tanggal:</strong> ${receipt.receiptDate}</p>

                            <p><strong>No. Dokumen:</strong> ${receipt.documentNumber}</p>

                            <p><strong>Site:</strong> ${receipt.siteName || '-'}</p>

                            <h5 class="font-bold text-md mt-4 mb-2">Daftar Barang:</h5>

                            <ul class="list-disc pl-5">

                        `;

                        receipt.items.forEach(item => {

                            detailMessage += `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`;

                            detailMessage += `<ul class="list-circle pl-8 text-sm text-gray-600">

                                <li>Kode: ${item.itemCode || '-'}</li>

                                <li>Serial: ${item.serialNumber || '-'}</li>

                                <li>Asset: ${item.assetNumber || '-'}</li>

                            </ul>`;

                        });

                        detailMessage += `</ul>`;

                        showMessageBox(detailMessage);

                    } else {

                        showMessageBox('Detail penerimaan tidak ditemukan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal mengambil detail penerimaan:', event.target.errorCode);

                };

            }



            function deleteReceipt(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus transaksi penerimaan ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_EXTERNAL_RECEIPTS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_RECEIPTS);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Transaksi penerimaan dengan ID ${id} berhasil dihapus.`);

                    displayReceipts();

                    showMessageBox('Transaksi penerimaan berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus transaksi penerimaan:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus transaksi penerimaan.');

                };

            }



            function addCurrentPurchaseItemToList() {

                const itemName = currentPurchaseItemNameSelect.value.trim();

                const brand = currentPurchaseItemBrandInput.value.trim();

                const itemCode = currentPurchaseItemCodeInput.value.trim();

                const serialNumber = currentPurchaseItemSerialInput.value.trim();

                const assetNumber = currentPurchaseItemAssetInput.value.trim();

                const quantity = parseInt(currentPurchaseItemQtyInput.value);

                const notes = currentPurchaseItemNotesInput.value.trim();



                if (!itemName || isNaN(quantity) || quantity <= 0) {

                    showMessageBox('Nama Barang dan Qty (harus > 0) harus diisi untuk item pembelian!');

                    return;

                }



                const newItem = {

                    itemName, brand, itemCode, serialNumber, assetNumber, quantity, notes

                };



                if (editingCurrentPurchaseItemIndex !== null) {

                    currentPurchaseItems[editingCurrentPurchaseItemIndex] = newItem;

                    editingCurrentPurchaseItemIndex = null;

                    addCurrentPurchaseItemToListBtn.textContent = 'Tambah ke Daftar';

                    cancelEditCurrentPurchaseItemBtn.classList.add('hidden');

                    showMessageBox('Item berhasil diperbarui di daftar pembelian!');

                } else {

                    currentPurchaseItems.push(newItem);

                    showMessageBox('Item berhasil ditambahkan ke daftar pembelian!');

                }

                clearCurrentPurchaseItemInputs();

                displayCurrentPurchaseItems();

            }



            function displayCurrentPurchaseItems() {

                currentPurchaseItemsTableBody.innerHTML = '';

                currentPurchaseItems.forEach((item, index) => {

                    const row = currentPurchaseItemsTableBody.insertRow();

                    row.className = 'hover:bg-gray-50';

                    row.innerHTML = `

                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.itemName}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.brand || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.quantity}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.notes || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                            <button data-index="${index}" class="edit-current-item-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                            <button data-index="${index}" class="delete-current-item-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                        </td>

                    `;

                    row.querySelector('.edit-current-item-btn').addEventListener('click', () => editCurrentPurchaseItem(index));

                    row.querySelector('.delete-current-item-btn').addEventListener('click', () => deleteCurrentPurchaseItem(index));

                });

            }



            function editCurrentPurchaseItem(index) {

                const itemToEdit = currentPurchaseItems[index];

                currentPurchaseItemNameSelect.value = itemToEdit.itemName;

                currentPurchaseItemBrandInput.value = itemToEdit.brand;

                currentPurchaseItemCodeInput.value = itemToEdit.itemCode;

                currentPurchaseItemSerialInput.value = itemToEdit.serialNumber;

                currentPurchaseItemAssetInput.value = itemToEdit.assetNumber;

                currentPurchaseItemQtyInput.value = itemToEdit.quantity;

                currentPurchaseItemNotesInput.value = itemToEdit.notes;

                editingCurrentPurchaseItemIndex = index;

                addCurrentPurchaseItemToListBtn.textContent = 'Perbarui Item';

                cancelEditCurrentPurchaseItemBtn.classList.remove('hidden');

                showMessageBox('Mode Edit Item: Ubah detail di atas dan klik Perbarui Item.');

            }



            function deleteCurrentPurchaseItem(index) {

                if (confirm('Apakah kamu yakin ingin menghapus item ini dari daftar pembelian?')) {

                    currentPurchaseItems.splice(index, 1);

                    displayCurrentPurchaseItems();

                    showMessageBox('Item berhasil dihapus dari daftar pembelian!');

                }

            }



            function clearCurrentPurchaseItemInputs() {

                currentPurchaseItemNameSelect.value = '';

                currentPurchaseItemBrandInput.value = '';

                currentPurchaseItemCodeInput.value = '';

                currentPurchaseItemSerialInput.value = '';

                currentPurchaseItemAssetInput.value = '';

                currentPurchaseItemQtyInput.value = '';

                currentPurchaseItemNotesInput.value = '';

            }



            function savePurchaseTransaction() {

                const date = purchaseDateInput.value;

                const docNum = purchaseDocNumInput.value.trim();

                const supplierName = purchaseSupplierNameSelect.value.trim();



                if (!date || !docNum || !supplierName) {

                    showMessageBox('Tanggal, Nomor Dokumen, dan Nama Supplier harus diisi!');

                    return;

                }

                if (currentPurchaseItems.length === 0) {

                    showMessageBox('Setidaknya harus ada satu barang yang dibeli!');

                    return;

                }

                const transaction = db.transaction([STORE_EXTERNAL_PURCHASES], 'readwrite');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_PURCHASES);

                const newPurchase = {

                    purchaseDate: date, documentNumber: docNum, supplierName: supplierName, items: currentPurchaseItems, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newPurchase);

                request.onsuccess = () => {

                    console.log('Transaksi pembelian berhasil disimpan.');

                    clearPurchaseForm();

                    displayPurchases();

                    showMessageBox('Pembelian berhasil dicatat!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan transaksi pembelian:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan transaksi pembelian.');

                };

            }



            function clearPurchaseForm() {

                purchaseDateInput.value = '';

                purchaseDocNumInput.value = '';

                purchaseSupplierNameSelect.value = '';

                currentPurchaseItems = [];

                editingCurrentPurchaseItemIndex = null;

                clearCurrentPurchaseItemInputs();

                displayCurrentPurchaseItems();

                addCurrentPurchaseItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentPurchaseItemBtn.classList.add('hidden');

            }



            function displayPurchases() {

                purchasesTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_EXTERNAL_PURCHASES], 'readonly');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_PURCHASES);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const purchase = cursor.value;

                        const row = purchasesTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${purchase.purchaseDate}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${purchase.documentNumber}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${purchase.supplierName}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${purchase.items.length}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${purchase.id}" class="view-purchase-btn bg-blue-400 hover:bg-blue-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Lihat Detail</button>

                                <button data-id="${purchase.id}" class="delete-purchase-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.view-purchase-btn').addEventListener('click', () => viewPurchaseDetail(purchase.id));

                        row.querySelector('.delete-purchase-btn').addEventListener('click', () => deletePurchase(purchase.id));

                        cursor.continue();

                    } else {

                        console.log('Semua pembelian telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan pembelian:', event.target.errorCode);

                };

            }



            function viewPurchaseDetail(id) {

                const transaction = db.transaction([STORE_EXTERNAL_PURCHASES], 'readonly');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_PURCHASES);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const purchase = event.target.result;

                    if (purchase) {

                        let detailMessage = `

                            <h4 class="font-bold text-lg mb-2">Detail Pembelian #${purchase.id}</h4>

                            <p><strong>Tanggal:</strong> ${purchase.purchaseDate}</p>

                            <p><strong>No. Dokumen:</strong> ${purchase.documentNumber}</p>

                            <p><strong>Supplier:</strong> ${purchase.supplierName}</p>

                            <h5 class="font-bold text-md mt-4 mb-2">Daftar Barang:</h5>

                            <ul class="list-disc pl-5">

                        `;

                        purchase.items.forEach(item => {

                            detailMessage += `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`;

                            detailMessage += `<ul class="list-circle pl-8 text-sm text-gray-600">

                                <li>Kode: ${item.itemCode || '-'}</li>

                                <li>Serial: ${item.serialNumber || '-'}</li>

                                <li>Asset: ${item.assetNumber || '-'}</li>

                            </ul>`;

                        });

                        detailMessage += `</ul>`;

                        showMessageBox(detailMessage);

                    } else {

                        showMessageBox('Detail pembelian tidak ditemukan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal mengambil detail pembelian:', event.target.errorCode);

                };

            }



            function deletePurchase(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus transaksi pembelian ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_EXTERNAL_PURCHASES], 'readwrite');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_PURCHASES);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Transaksi pembelian dengan ID ${id} berhasil dihapus.`);

                    displayPurchases();

                    showMessageBox('Transaksi pembelian berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus transaksi pembelian:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus transaksi pembelian.');

                };

            }



            function addCurrentShipmentItemToList() {

                const itemName = currentShipmentItemNameSelect.value.trim();

                const brand = currentShipmentItemBrandInput.value.trim();

                const itemCode = currentShipmentItemCodeInput.value.trim();

                const serialNumber = currentShipmentItemSerialInput.value.trim();

                const assetNumber = currentShipmentItemAssetInput.value.trim();

                const quantity = parseInt(currentShipmentItemQtyInput.value);

                const notes = currentShipmentItemNotesInput.value.trim();



                if (!itemName || !brand || !itemCode || isNaN(quantity) || quantity <= 0) {

                    showMessageBox('Nama Barang, Brand, Kode Barang, dan Qty (harus > 0) harus diisi untuk item pengiriman!');

                    return;

                }



                const newItem = {

                    itemName, brand, itemCode, serialNumber, assetNumber, quantity, notes

                };



                if (editingCurrentShipmentItemIndex !== null) {

                    currentShipmentItems[editingCurrentShipmentItemIndex] = newItem;

                    editingCurrentShipmentItemIndex = null;

                    addCurrentShipmentItemToListBtn.textContent = 'Tambah ke Daftar';

                    cancelEditCurrentShipmentItemBtn.classList.add('hidden');

                    showMessageBox('Item berhasil diperbarui di daftar pengiriman!');

                } else {

                    currentShipmentItems.push(newItem);

                    showMessageBox('Item berhasil ditambahkan ke daftar pengiriman!');

                }

                clearCurrentShipmentItemInputs();

                displayCurrentShipmentItems();

            }



            function displayCurrentShipmentItems() {

                currentShipmentItemsTableBody.innerHTML = '';

                currentShipmentItems.forEach((item, index) => {

                    const row = currentShipmentItemsTableBody.insertRow();

                    row.className = 'hover:bg-gray-50';

                    row.innerHTML = `

                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.itemName}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.brand || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.quantity}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.notes || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                            <button data-index="${index}" class="edit-current-item-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                            <button data-index="${index}" class="delete-current-item-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                        </td>

                    `;

                    row.querySelector('.edit-current-item-btn').addEventListener('click', () => editCurrentShipmentItem(index));

                    row.querySelector('.delete-current-item-btn').addEventListener('click', () => deleteCurrentShipmentItem(index));

                });

            }



            function editCurrentShipmentItem(index) {

                const itemToEdit = currentShipmentItems[index];

                currentShipmentItemNameSelect.value = itemToEdit.itemName;

                currentShipmentItemBrandInput.value = itemToEdit.brand;

                currentShipmentItemCodeInput.value = itemToEdit.itemCode;

                currentShipmentItemSerialInput.value = itemToEdit.serialNumber;

                currentShipmentItemAssetInput.value = itemToEdit.assetNumber;

                currentShipmentItemQtyInput.value = itemToEdit.quantity;

                currentShipmentItemNotesInput.value = itemToEdit.notes;

                editingCurrentShipmentItemIndex = index;

                addCurrentShipmentItemToListBtn.textContent = 'Perbarui Item';

                cancelEditCurrentShipmentItemBtn.classList.remove('hidden');

                showMessageBox('Mode Edit Item: Ubah detail di atas dan klik Perbarui Item.');

            }



            function deleteCurrentShipmentItem(index) {

                if (confirm('Apakah kamu yakin ingin menghapus item ini dari daftar pengiriman?')) {

                    currentShipmentItems.splice(index, 1);

                    displayCurrentShipmentItems();

                    showMessageBox('Item berhasil dihapus dari daftar pengiriman!');

                }

            }



            function clearCurrentShipmentItemInputs() {

                currentShipmentItemNameSelect.value = '';

                currentShipmentItemBrandInput.value = '';

                currentShipmentItemCodeInput.value = '';

                currentShipmentItemSerialInput.value = '';

                currentShipmentItemAssetInput.value = '';

                currentShipmentItemQtyInput.value = '';

                currentShipmentItemNotesInput.value = '';

            }



            function saveShipmentTransaction() {

                const date = shipmentDateInput.value;

                const docNum = shipmentDocNumInput.value.trim();

                const destinationSite = shipmentDestinationSiteSelect.value.trim();



                if (!date || !docNum || !destinationSite) {

                    showMessageBox('Tanggal, Nomor Dokumen, dan Nama Site Tujuan harus diisi!');

                    return;

                }

                if (currentShipmentItems.length === 0) {

                    showMessageBox('Setidaknya harus ada satu barang untuk dikirim!');

                    return;

                }

                const transaction = db.transaction([STORE_EXTERNAL_SHIPMENTS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_SHIPMENTS);

                const newShipment = {

                    shipmentDate: date, documentNumber: docNum, destinationSite: destinationSite, items: currentShipmentItems, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newShipment);

                request.onsuccess = () => {

                    console.log('Transaksi pengiriman berhasil disimpan.');

                    clearShipmentForm();

                    displayShipments();

                    showMessageBox('Pengiriman berhasil dicatat!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan transaksi pengiriman:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan transaksi pengiriman.');

                };

            }



            function clearShipmentForm() {

                shipmentDateInput.value = '';

                shipmentDocNumInput.value = '';

                shipmentDestinationSiteSelect.value = '';

                currentShipmentItems = [];

                editingCurrentShipmentItemIndex = null;

                clearCurrentShipmentItemInputs();

                displayCurrentShipmentItems();

                addCurrentShipmentItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentShipmentItemBtn.classList.add('hidden');

            }



            function displayShipments() {

                shipmentsTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_EXTERNAL_SHIPMENTS], 'readonly');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_SHIPMENTS);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const shipment = cursor.value;

                        const row = shipmentsTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${shipment.shipmentDate}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${shipment.documentNumber}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${shipment.destinationSite || '-'}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${shipment.items.length}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${shipment.id}" class="view-shipment-btn bg-blue-400 hover:bg-blue-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Lihat Detail</button>

                                <button data-id="${shipment.id}" class="delete-shipment-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.view-shipment-btn').addEventListener('click', () => viewShipmentDetail(shipment.id));

                        row.querySelector('.delete-shipment-btn').addEventListener('click', () => deleteShipment(shipment.id));

                        cursor.continue();

                    } else {

                        console.log('Semua pengiriman telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan pengiriman:', event.target.errorCode);

                };

            }



            function viewShipmentDetail(id) {

                const transaction = db.transaction([STORE_EXTERNAL_SHIPMENTS], 'readonly');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_SHIPMENTS);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const shipment = event.target.result;

                    if (shipment) {

                        let detailMessage = `

                            <h4 class="font-bold text-lg mb-2">Detail Pengiriman #${shipment.id}</h4>

                            <p><strong>Tanggal:</strong> ${shipment.shipmentDate}</p>

                            <p><strong>No. Dokumen:</strong> ${shipment.documentNumber}</p>

                            <p><strong>Site Tujuan:</strong> ${shipment.destinationSite || '-'}</p>

                            <h5 class="font-bold text-md mt-4 mb-2">Daftar Barang:</h5>

                            <ul class="list-disc pl-5">

                        `;

                        shipment.items.forEach(item => {

                            detailMessage += `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`;

                            detailMessage += `<ul class="list-circle pl-8 text-sm text-gray-600">

                                <li>Kode: ${item.itemCode || '-'}</li>

                                <li>Serial: ${item.serialNumber || '-'}</li>

                                <li>Asset: ${item.assetNumber || '-'}</li>

                            </ul>`;

                        });

                        detailMessage += `</ul>`;

                        showMessageBox(detailMessage);

                    } else {

                        showMessageBox('Detail pengiriman tidak ditemukan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal mengambil detail pengiriman:', event.target.errorCode);

                };

            }



            function deleteShipment(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus transaksi pengiriman ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_EXTERNAL_SHIPMENTS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_EXTERNAL_SHIPMENTS);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Transaksi pengiriman dengan ID ${id} berhasil dihapus.`);

                    displayShipments();

                    showMessageBox('Transaksi pengiriman berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus transaksi pengiriman:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus transaksi pengiriman.');

                };

            }



            function addCurrentOtherExternalItemToList() {

                const itemName = currentOtherExternalItemNameSelect.value.trim();

                const brand = currentOtherExternalItemBrandInput.value.trim();

                const itemCode = currentOtherExternalItemCodeInput.value.trim();

                const serialNumber = currentOtherExternalItemSerialInput.value.trim();

                const assetNumber = currentOtherExternalItemAssetInput.value.trim();

                const quantity = parseInt(currentOtherExternalItemQtyInput.value);

                const notes = currentOtherExternalItemNotesInput.value.trim();



                if (!itemName || isNaN(quantity) || quantity <= 0) {

                    showMessageBox('Nama Barang dan Qty (harus > 0) harus diisi untuk item transaksi lain!');

                    return;

                }



                const newItem = {

                    itemName, brand, itemCode, serialNumber, assetNumber, quantity, notes

                };



                if (editingCurrentOtherExternalItemIndex !== null) {

                    currentOtherExternalItems[editingCurrentOtherExternalItemIndex] = newItem;

                    editingCurrentOtherExternalItemIndex = null;

                    addCurrentOtherExternalItemToListBtn.textContent = 'Tambah ke Daftar';

                    cancelEditCurrentOtherExternalItemBtn.classList.add('hidden');

                    showMessageBox('Item berhasil diperbarui di daftar transaksi lain!');

                } else {

                    currentOtherExternalItems.push(newItem);

                    showMessageBox('Item berhasil ditambahkan ke daftar transaksi lain!');

                }

                clearCurrentOtherExternalItemInputs();

                displayCurrentOtherExternalItems();

            }



            function displayCurrentOtherExternalItems() {

                currentOtherExternalItemsTableBody.innerHTML = '';

                currentOtherExternalItems.forEach((item, index) => {

                    const row = currentOtherExternalItemsTableBody.insertRow();

                    row.className = 'hover:bg-gray-50';

                    row.innerHTML = `

                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.itemName}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.brand || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.quantity}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.notes || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                            <button data-index="${index}" class="edit-current-item-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                            <button data-index="${index}" class="delete-current-item-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                        </td>

                    `;

                    row.querySelector('.edit-current-item-btn').addEventListener('click', () => editCurrentOtherExternalItem(index));

                    row.querySelector('.delete-current-item-btn').addEventListener('click', () => deleteCurrentOtherExternalItem(index));

                });

            }



            function editCurrentOtherExternalItem(index) {

                const itemToEdit = currentOtherExternalItems[index];

                currentOtherExternalItemNameSelect.value = itemToEdit.itemName;

                currentOtherExternalItemBrandInput.value = itemToEdit.brand;

                currentOtherExternalItemCodeInput.value = itemToEdit.itemCode;

                currentOtherExternalItemSerialInput.value = itemToEdit.serialNumber;

                currentOtherExternalItemAssetInput.value = itemToEdit.assetNumber;

                currentOtherExternalItemQtyInput.value = itemToEdit.quantity;

                currentOtherExternalItemNotesInput.value = itemToEdit.notes;

                editingCurrentOtherExternalItemIndex = index;

                addCurrentOtherExternalItemToListBtn.textContent = 'Perbarui Item';

                cancelEditCurrentOtherExternalItemBtn.classList.remove('hidden');

                showMessageBox('Mode Edit Item: Ubah detail di atas dan klik Perbarui Item.');

            }



            function deleteCurrentOtherExternalItem(index) {

                if (confirm('Apakah kamu yakin ingin menghapus item ini dari daftar transaksi lain?')) {

                    currentOtherExternalItems.splice(index, 1);

                    displayCurrentOtherExternalItems();

                    showMessageBox('Item berhasil dihapus dari daftar transaksi lain!');

                }

            }



            function clearCurrentOtherExternalItemInputs() {

                currentOtherExternalItemNameSelect.value = '';

                currentOtherExternalItemBrandInput.value = '';

                currentOtherExternalItemCodeInput.value = '';

                currentOtherExternalItemSerialInput.value = '';

                currentOtherExternalItemAssetInput.value = '';

                currentOtherExternalItemQtyInput.value = '';

                currentOtherExternalItemNotesInput.value = '';

            }



            function saveOtherExternalTransaction() {

                const date = otherExternalDateInput.value;

                const docNum = otherExternalDocNumInput.value.trim();

                const partyName = otherExternalPartyNameInput.value.trim();

                const transactionType = otherExternalTransactionTypeSelect.value.trim();



                if (!date || !docNum || !partyName || !transactionType) {

                    showMessageBox('Tanggal, Nomor Dokumen, Nama Pihak Terkait, dan Jenis Transaksi harus diisi!');

                    return;

                }

                if (currentOtherExternalItems.length === 0) {

                    showMessageBox('Setidaknya harus ada satu barang dalam transaksi ini!');

                    return;

                }

                const transaction = db.transaction([STORE_OTHER_EXTERNAL_TRANSACTIONS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_OTHER_EXTERNAL_TRANSACTIONS);

                const newOtherExternalTransaction = {

                    otherExternalDate: date, documentNumber: docNum, partyName: partyName, transactionType: transactionType, items: currentOtherExternalItems, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newOtherExternalTransaction);

                request.onsuccess = () => {

                    console.log('Transaksi lain eksternal berhasil disimpan.');

                    clearOtherExternalForm();

                    displayOtherExternalTransactions();

                    showMessageBox('Transaksi lain eksternal berhasil dicatat!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan transaksi lain eksternal:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan transaksi lain eksternal.');

                };

            }



            function clearOtherExternalForm() {

                otherExternalDateInput.value = '';

                otherExternalDocNumInput.value = '';

                otherExternalPartyNameInput.value = '';

                otherExternalTransactionTypeSelect.value = '';

                currentOtherExternalItems = [];

                editingCurrentOtherExternalItemIndex = null;

                clearCurrentOtherExternalItemInputs();

                displayCurrentOtherExternalItems();

                addCurrentOtherExternalItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentOtherExternalItemBtn.classList.add('hidden');

            }



            function displayOtherExternalTransactions() {

                otherExternalTransactionsTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_OTHER_EXTERNAL_TRANSACTIONS], 'readonly');

                const objectStore = transaction.objectStore(STORE_OTHER_EXTERNAL_TRANSACTIONS);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const otherExternalTransaction = cursor.value;

                        const row = otherExternalTransactionsTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${otherExternalTransaction.otherExternalDate}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherExternalTransaction.documentNumber}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherExternalTransaction.partyName}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherExternalTransaction.transactionType}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherExternalTransaction.items.length}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${otherExternalTransaction.id}" class="view-other-external-btn bg-blue-400 hover:bg-blue-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Lihat Detail</button>

                                <button data-id="${otherExternalTransaction.id}" class="delete-other-external-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.view-other-external-btn').addEventListener('click', () => viewOtherExternalDetail(otherExternalTransaction.id));

                        row.querySelector('.delete-other-external-btn').addEventListener('click', () => deleteOtherExternal(otherExternalTransaction.id));

                        cursor.continue();

                    } else {

                        console.log('Semua transaksi lain eksternal telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan transaksi lain eksternal:', event.target.errorCode);

                };

            }



            function viewOtherExternalDetail(id) {

                const transaction = db.transaction([STORE_OTHER_EXTERNAL_TRANSACTIONS], 'readonly');

                const objectStore = transaction.objectStore(STORE_OTHER_EXTERNAL_TRANSACTIONS);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const otherExternalTransaction = event.target.result;

                    if (otherExternalTransaction) {

                        let detailMessage = `

                            <h4 class="font-bold text-lg mb-2">Detail Transaksi Lain Eksternal #${otherExternalTransaction.id}</h4>

                            <p><strong>Tanggal:</strong> ${otherExternalTransaction.otherExternalDate}</p>

                            <p><strong>No. Dokumen:</strong> ${otherExternalTransaction.documentNumber}</p>

                            <p><strong>Pihak Terkait:</strong> ${otherExternalTransaction.partyName}</p>

                            <p><strong>Jenis Transaksi:</strong> ${otherExternalTransaction.transactionType}</p>

                            <h5 class="font-bold text-md mt-4 mb-2">Daftar Barang:</h5>

                            <ul class="list-disc pl-5">

                        `;

                        otherExternalTransaction.items.forEach(item => {

                            detailMessage += `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`;

                            detailMessage += `<ul class="list-circle pl-8 text-sm text-gray-600">

                                <li>Kode: ${item.itemCode || '-'}</li>

                                <li>Serial: ${item.serialNumber || '-'}</li>

                                <li>Asset: ${item.assetNumber || '-'}</li>

                            </ul>`;

                        });

                        detailMessage += `</ul>`;

                        showMessageBox(detailMessage);

                    } else {

                        showMessageBox('Detail transaksi lain eksternal tidak ditemukan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal mengambil detail transaksi lain eksternal:', event.target.errorCode);

                };

            }



            function deleteOtherExternal(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus transaksi lain eksternal ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_OTHER_EXTERNAL_TRANSACTIONS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_OTHER_EXTERNAL_TRANSACTIONS);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Transaksi lain eksternal dengan ID ${id} berhasil dihapus.`);

                    displayOtherExternalTransactions();

                    showMessageBox('Transaksi lain eksternal berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus transaksi lain eksternal:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus transaksi lain eksternal.');

                };

            }



            function addCurrentOtherInternalItemToList() {

                const itemName = currentOtherInternalItemNameSelect.value.trim();

                const brand = currentOtherInternalItemBrandInput.value.trim();

                const itemCode = currentOtherInternalItemCodeInput.value.trim();

                const serialNumber = currentOtherInternalItemSerialInput.value.trim();

                const assetNumber = currentOtherInternalItemAssetInput.value.trim();

                const quantity = parseInt(currentOtherInternalItemQtyInput.value);

                const notes = currentOtherInternalItemNotesInput.value.trim();



                if (!itemName || isNaN(quantity) || quantity <= 0) {

                    showMessageBox('Nama Barang dan Qty (harus > 0) harus diisi untuk item transaksi lain!');

                    return;

                }



                const newItem = {

                    itemName, brand, itemCode, serialNumber, assetNumber, quantity, notes

                };



                if (editingCurrentOtherInternalItemIndex !== null) {

                    currentOtherInternalItems[editingCurrentOtherInternalItemIndex] = newItem;

                    editingCurrentOtherInternalItemIndex = null;

                    addCurrentOtherInternalItemToListBtn.textContent = 'Tambah ke Daftar';

                    cancelEditCurrentOtherInternalItemBtn.classList.add('hidden');

                    showMessageBox('Item berhasil diperbarui di daftar transaksi lain!');

                } else {

                    currentOtherInternalItems.push(newItem);

                    showMessageBox('Item berhasil ditambahkan ke daftar transaksi lain!');

                }

                clearCurrentOtherInternalItemInputs();

                displayCurrentOtherInternalItems();

            }



            function displayCurrentOtherInternalItems() {

                currentOtherInternalItemsTableBody.innerHTML = '';

                currentOtherInternalItems.forEach((item, index) => {

                    const row = currentOtherInternalItemsTableBody.insertRow();

                    row.className = 'hover:bg-gray-50';

                    row.innerHTML = `

                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.itemName}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.brand || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.quantity}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.notes || '-'}</td>

                        <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                            <button data-index="${index}" class="edit-current-item-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                            <button data-index="${index}" class="delete-current-item-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                        </td>

                    `;

                    row.querySelector('.edit-current-item-btn').addEventListener('click', () => editCurrentOtherInternalItem(index));

                    row.querySelector('.delete-current-item-btn').addEventListener('click', () => deleteCurrentOtherInternalItem(index));

                });

            }



            function editCurrentOtherInternalItem(index) {

                const itemToEdit = currentOtherInternalItems[index];

                currentOtherInternalItemNameSelect.value = itemToEdit.itemName;

                currentOtherInternalItemBrandInput.value = itemToEdit.brand;

                currentOtherInternalItemCodeInput.value = itemToEdit.itemCode;

                currentOtherInternalItemSerialInput.value = itemToEdit.serialNumber;

                currentOtherInternalItemAssetInput.value = itemToEdit.assetNumber;

                currentOtherInternalItemQtyInput.value = itemToEdit.quantity;

                currentOtherInternalItemNotesInput.value = itemToEdit.notes;

                editingCurrentOtherInternalItemIndex = index;

                addCurrentOtherInternalItemToListBtn.textContent = 'Perbarui Item';

                cancelEditCurrentOtherInternalItemBtn.classList.remove('hidden');

                showMessageBox('Mode Edit Item: Ubah detail di atas dan klik Perbarui Item.');

            }



            function deleteCurrentOtherInternalItem(index) {

                if (confirm('Apakah kamu yakin ingin menghapus item ini dari daftar transaksi lain?')) {

                    currentOtherInternalItems.splice(index, 1);

                    displayCurrentOtherInternalItems();

                    showMessageBox('Item berhasil dihapus dari daftar transaksi lain!');

                }

            }



            function clearCurrentOtherInternalItemInputs() {

                currentOtherInternalItemNameSelect.value = '';

                currentOtherInternalItemBrandInput.value = '';

                currentOtherInternalItemCodeInput.value = '';

                currentOtherInternalItemSerialInput.value = '';

                currentOtherInternalItemAssetInput.value = '';

                currentOtherInternalItemQtyInput.value = '';

                currentOtherInternalItemNotesInput.value = '';

            }



            function saveOtherInternalTransaction() {

                const date = otherInternalDateInput.value;

                const docNum = otherInternalDocNumInput.value.trim();

                const partyName = otherInternalPartyNameInput.value.trim();

                const transactionType = otherInternalTransactionTypeSelect.value.trim();



                if (!date || !docNum || !partyName || !transactionType) {

                    showMessageBox('Tanggal, Nomor Dokumen, Nama Pihak Terkait, dan Jenis Transaksi harus diisi!');

                    return;

                }

                if (currentOtherInternalItems.length === 0) {

                    showMessageBox('Setidaknya harus ada satu barang dalam transaksi ini!');

                    return;

                }

                const transaction = db.transaction([STORE_OTHER_INTERNAL_TRANSACTIONS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_OTHER_INTERNAL_TRANSACTIONS);

                const newOtherInternalTransaction = {

                    otherInternalDate: date, documentNumber: docNum, partyName: partyName, transactionType: transactionType, items: currentOtherInternalItems, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newOtherInternalTransaction);

                request.onsuccess = () => {

                    console.log('Transaksi lain internal berhasil disimpan.');

                    clearOtherInternalForm();

                    displayOtherInternalTransactions();

                    showMessageBox('Transaksi lain internal berhasil dicatat!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan transaksi lain internal:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan transaksi lain internal.');

                };

            }



            function clearOtherInternalForm() {

                otherInternalDateInput.value = '';

                otherInternalDocNumInput.value = '';

                otherInternalPartyNameInput.value = '';

                otherInternalTransactionTypeSelect.value = '';

                currentOtherInternalItems = [];

                editingCurrentOtherInternalItemIndex = null;

                clearCurrentOtherInternalItemInputs();

                displayCurrentOtherInternalItems();

                addCurrentOtherInternalItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentOtherInternalItemBtn.classList.add('hidden');

            }



            function displayOtherInternalTransactions() {

                otherInternalTransactionsTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_OTHER_INTERNAL_TRANSACTIONS], 'readonly');

                const objectStore = transaction.objectStore(STORE_OTHER_INTERNAL_TRANSACTIONS);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const otherInternalTransaction = cursor.value;

                        const row = otherInternalTransactionsTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${otherInternalTransaction.otherInternalDate}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherInternalTransaction.documentNumber}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherInternalTransaction.partyName}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherInternalTransaction.transactionType}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${otherInternalTransaction.items.length}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${otherInternalTransaction.id}" class="view-other-internal-btn bg-blue-400 hover:bg-blue-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Lihat Detail</button>

                                <button data-id="${otherInternalTransaction.id}" class="delete-other-internal-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.view-other-internal-btn').addEventListener('click', () => viewOtherInternalDetail(otherInternalTransaction.id));

                        row.querySelector('.delete-other-internal-btn').addEventListener('click', () => deleteOtherInternal(otherInternalTransaction.id));

                        cursor.continue();

                    } else {

                        console.log('Semua transaksi lain internal telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan transaksi lain internal:', event.target.errorCode);

                };

            }



            function viewOtherInternalDetail(id) {

                const transaction = db.transaction([STORE_OTHER_INTERNAL_TRANSACTIONS], 'readonly');

                const objectStore = transaction.objectStore(STORE_OTHER_INTERNAL_TRANSACTIONS);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const otherInternalTransaction = event.target.result;

                    if (otherInternalTransaction) {

                        let detailMessage = `

                            <h4 class="font-bold text-lg mb-2">Detail Transaksi Lain Internal #${otherInternalTransaction.id}</h4>

                            <p><strong>Tanggal:</strong> ${otherInternalTransaction.otherInternalDate}</p>

                            <p><strong>No. Dokumen:</strong> ${otherInternalTransaction.documentNumber}</p>

                            <p><strong>Pihak Terkait:</strong> ${otherInternalTransaction.partyName}</p>

                            <p><strong>Jenis Transaksi:</strong> ${otherInternalTransaction.transactionType}</p>

                            <h5 class="font-bold text-md mt-4 mb-2">Daftar Barang:</h5>

                            <ul class="list-disc pl-5">

                        `;

                        otherInternalTransaction.items.forEach(item => {

                            detailMessage += `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`;

                            detailMessage += `<ul class="list-circle pl-8 text-sm text-gray-600">

                                <li>Kode: ${item.itemCode || '-'}</li>

                                <li>Serial: ${item.serialNumber || '-'}</li>

                                <li>Asset: ${item.assetNumber || '-'}</li>

                            </ul>`;

                        });

                        detailMessage += `</ul>`;

                        showMessageBox(detailMessage);

                    } else {

                        showMessageBox('Detail transaksi lain internal tidak ditemukan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal mengambil detail transaksi lain internal:', event.target.errorCode);

                };

            }



            function deleteOtherInternal(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus transaksi lain internal ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_OTHER_INTERNAL_TRANSACTIONS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_OTHER_INTERNAL_TRANSACTIONS);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Transaksi lain internal dengan ID ${id} berhasil dihapus.`);

                    displayOtherInternalTransactions();

                    showMessageBox('Transaksi lain internal berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus transaksi lain internal:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus transaksi lain internal.');

                };

            }



            function addSupplier() {

                const name = supplierNameInput.value.trim();

                const contact = supplierContactInput.value.trim();

                const address = supplierAddressInput.value.trim();

                if (!name || !contact || !address) {

                    showMessageBox('Nama Supplier, Nomor Kontak, dan Alamat harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_SUPPLIERS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_SUPPLIERS);

                const newSupplier = {

                    supplierName: name, contactNumber: contact, address: address, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newSupplier);

                request.onsuccess = () => {

                    console.log('Supplier berhasil disimpan.');

                    clearSupplierForm();

                    displaySuppliers();

                    showMessageBox('Supplier berhasil ditambahkan!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan supplier:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan supplier. Mungkin nama supplier sudah ada.');

                };

            }



            function updateSupplier(id, name, contact, address) {

                if (!name || !contact || !address) {

                    showMessageBox('Nama Supplier, Nomor Kontak, dan Alamat harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_SUPPLIERS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_SUPPLIERS);

                const getRequest = objectStore.get(id);

                getRequest.onsuccess = (event) => {

                    const supplier = event.target.result;

                    if (supplier) {

                        supplier.supplierName = name;

                        supplier.contactNumber = contact;

                        supplier.address = address;

                        supplier.timestamp = new Date().getTime();

                        const updateRequest = objectStore.put(supplier);

                        updateRequest.onsuccess = () => {

                            console.log(`Supplier dengan ID ${id} berhasil diperbarui.`);

                            clearSupplierForm();

                            displaySuppliers();

                            resetSupplierFormForAdd();

                            showMessageBox('Supplier berhasil diperbarui!');

                        };

                        updateRequest.onerror = (event) => {

                            console.error('Gagal memperbarui supplier:', event.target.errorCode);

                            showMessageBox('Error: Gagal memperbarui supplier. Mungkin nama supplier sudah ada.');

                        };

                    } else {

                        showMessageBox('Supplier tidak ditemukan untuk diperbarui.');

                    }

                };

                getRequest.onerror = (event) => {

                    console.error('Gagal mengambil supplier untuk diperbarui:', event.target.errorCode);

                };

            }



            function displaySuppliers() {

                suppliersTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_SUPPLIERS], 'readonly');

                const objectStore = transaction.objectStore(STORE_SUPPLIERS);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const supplier = cursor.value;

                        const row = suppliersTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${supplier.supplierName}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${supplier.contactNumber}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${supplier.address}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${supplier.id}" class="edit-supplier-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                                <button data-id="${supplier.id}" class="delete-supplier-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.edit-supplier-btn').addEventListener('click', () => populateSupplierFormForEdit(supplier.id));

                        row.querySelector('.delete-supplier-btn').addEventListener('click', () => deleteSupplier(supplier.id));

                        cursor.continue();

                    } else {

                        console.log('Semua supplier telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan supplier:', event.target.errorCode);

                };

            }



            function populateSupplierFormForEdit(id) {

                const transaction = db.transaction([STORE_SUPPLIERS], 'readonly');

                const objectStore = transaction.objectStore(STORE_SUPPLIERS);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const supplier = event.target.result;

                    if (supplier) {

                        supplierNameInput.value = supplier.supplierName;

                        supplierContactInput.value = supplier.contactNumber;

                        supplierAddressInput.value = supplier.address;

                        editingSupplierId = supplier.id;

                        saveSupplierBtn.textContent = 'Perbarui Supplier';

                        saveSupplierBtn.classList.remove('bg-blue-600', 'hover:bg-blue-700');

                        saveSupplierBtn.classList.add('bg-green-600', 'hover:bg-green-700');

                        showMessageBox('Mode Edit: Isi form untuk memperbarui supplier.');

                    }

                };

            }



            function resetSupplierFormForAdd() {

                clearSupplierForm();

                editingSupplierId = null;

                saveSupplierBtn.textContent = 'Simpan Supplier';

                saveSupplierBtn.classList.remove('bg-green-600', 'hover:bg-green-700');

                saveSupplierBtn.classList.add('bg-blue-600', 'hover:bg-blue-700');

            }



            function deleteSupplier(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus supplier ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_SUPPLIERS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_SUPPLIERS);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Supplier dengan ID ${id} berhasil dihapus.`);

                    displaySuppliers();

                    showMessageBox('Supplier berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus supplier:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus supplier.');

                };

            }



            function clearSupplierForm() {

                supplierNameInput.value = '';

                supplierContactInput.value = '';

                supplierAddressInput.value = '';

            }



            function createMemberNameInput(memberName = '') {

                const div = document.createElement('div');

                div.className = 'flex items-center gap-2';

                div.innerHTML = `

                    <input type="text" value="${memberName}" placeholder="Nama Anggota" class="member-name-input flex-grow p-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-700">

                    <button class="remove-member-btn bg-red-400 hover:bg-red-500 text-white rounded-full h-6 w-6 flex items-center justify-center text-sm font-bold">&times;</button>

                `;

                div.querySelector('.remove-member-btn').addEventListener('click', () => div.remove());

                return div;

            }



            function addMemberNameHandler(memberName = '') {

                memberNamesContainer.appendChild(createMemberNameInput(memberName));

            }



            function getUserMemberNames() {

                const inputs = memberNamesContainer.querySelectorAll('.member-name-input');

                const memberNames = [];

                inputs.forEach(input => {

                    const name = input.value.trim();

                    if (name) {

                        memberNames.push(name);

                    }

                });

                return memberNames;

            }



            function addUser() {

                const name = userNameInput.value.trim();

                const section = userSectionInput.value.trim();

                const status = userStatusInput.value.trim();

                const memberNames = getUserMemberNames();



                if (!name || !section || !status || memberNames.length === 0) {

                    showMessageBox('Nama User, Section, Status, dan setidaknya satu Nama Anggota harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_USERS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_USERS);

                const newUser = {

                    userName: name, section: section, status: status, memberNames: memberNames, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newUser);

                request.onsuccess = () => {

                    console.log('User berhasil disimpan.');

                    clearUserForm();

                    displayUsers();

                    showMessageBox('User berhasil ditambahkan!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan user:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan user. Mungkin nama user sudah ada.');

                };

            }



            function updateUser(id, name, section, status, memberNames) {

                if (!name || !section || !status || memberNames.length === 0) {

                    showMessageBox('Nama User, Section, Status, dan setidaknya satu Nama Anggota harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_USERS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_USERS);

                const getRequest = objectStore.get(id);

                getRequest.onsuccess = (event) => {

                    const user = event.target.result;

                    if (user) {

                        user.userName = name;

                        user.section = section;

                        user.status = status;

                        user.memberNames = memberNames;

                        user.timestamp = new Date().getTime();

                        const updateRequest = objectStore.put(user);

                        updateRequest.onsuccess = () => {

                            console.log(`User dengan ID ${id} berhasil diperbarui.`);

                            clearUserForm();

                            displayUsers();

                            resetUserFormForAdd();

                            showMessageBox('User berhasil diperbarui!');

                        };

                        updateRequest.onerror = (event) => {

                            console.error('Gagal memperbarui user:', event.target.errorCode);

                            showMessageBox('Error: Gagal memperbarui user. Mungkin nama user sudah ada.');

                        };

                    } else {

                        showMessageBox('User tidak ditemukan untuk diperbarui.');

                    }

                };

                getRequest.onerror = (event) => {

                    console.error('Gagal mengambil user untuk diperbarui:', event.target.errorCode);

                };

            }



            function displayUsers() {

                usersTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_USERS], 'readonly');

                const objectStore = transaction.objectStore(STORE_USERS);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const user = cursor.value;

                        const row = usersTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${user.userName}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${user.section}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${user.status}</td>

                            <td class="px-6 py-4 text-sm text-gray-500">${user.memberNames.join(', ')}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${user.id}" class="edit-user-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                                <button data-id="${user.id}" class="delete-user-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.edit-user-btn').addEventListener('click', () => populateUserFormForEdit(user.id));

                        row.querySelector('.delete-user-btn').addEventListener('click', () => deleteUser(user.id));

                        cursor.continue();

                    } else {

                        console.log('Semua user telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan user:', event.target.errorCode);

                };

            }



            function populateUserFormForEdit(id) {

                const transaction = db.transaction([STORE_USERS], 'readonly');

                const objectStore = transaction.objectStore(STORE_USERS);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const user = event.target.result;

                    if (user) {

                        userNameInput.value = user.userName;

                        userSectionInput.value = user.section;

                        userStatusInput.value = user.status;

                        memberNamesContainer.innerHTML = '';

                        user.memberNames.forEach(name => addMemberNameHandler(name));

                        if (user.memberNames.length === 0) {

                            addMemberNameHandler();

                        }

                        editingUserId = user.id;

                        saveUserBtn.textContent = 'Perbarui User';

                        saveUserBtn.classList.remove('bg-blue-600', 'hover:bg-blue-700');

                        saveUserBtn.classList.add('bg-green-600', 'hover:bg-green-700');

                        showMessageBox('Mode Edit: Isi form untuk memperbarui user.');

                    }

                };

            }



            function resetUserFormForAdd() {

                clearUserForm();

                editingUserId = null;

                saveUserBtn.textContent = 'Simpan User';

                saveUserBtn.classList.remove('bg-green-600', 'hover:bg-green-700');

                saveUserBtn.classList.add('bg-blue-600', 'hover:bg-blue-700');

            }



            function deleteUser(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus user ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_USERS], 'readwrite');

                const objectStore = transaction.objectStore(STORE_USERS);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`User dengan ID ${id} berhasil dihapus.`);

                    displayUsers();

                    showMessageBox('User berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus user:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus user.');

                };

            }



            function clearUserForm() {

                userNameInput.value = '';

                userSectionInput.value = '';

                userStatusInput.value = '';

                memberNamesContainer.innerHTML = '';

                addMemberNameHandler();

            }



            function addSite() {

                const name = siteNameInput.value.trim();

                const pic = sitePICInput.value.trim();

                const address = siteAddressInput.value.trim();

                if (!name || !pic || !address) {

                    showMessageBox('Nama Site, PIC, dan Alamat harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_SITES], 'readwrite');

                const objectStore = transaction.objectStore(STORE_SITES);

                const newSite = {

                    siteName: name, pic: pic, address: address, timestamp: new Date().getTime()

                };

                const request = objectStore.add(newSite);

                request.onsuccess = () => {

                    console.log('Site berhasil disimpan.');

                    clearSiteForm();

                    displaySites();

                    showMessageBox('Site berhasil ditambahkan!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menyimpan site:', event.target.errorCode);

                    showMessageBox('Error: Gagal menyimpan site. Mungkin nama site sudah ada.');

                };

            }



            function updateSite(id, name, pic, address) {

                if (!name || !pic || !address) {

                    showMessageBox('Nama Site, PIC, dan Alamat harus diisi!');

                    return;

                }

                const transaction = db.transaction([STORE_SITES], 'readwrite');

                const objectStore = transaction.objectStore(STORE_SITES);

                const getRequest = objectStore.get(id);

                getRequest.onsuccess = (event) => {

                    const site = event.target.result;

                    if (site) {

                        site.siteName = name;

                        site.pic = pic;

                        site.address = address;

                        site.timestamp = new Date().getTime();

                        const updateRequest = objectStore.put(site);

                        updateRequest.onsuccess = () => {

                            console.log(`Site dengan ID ${id} berhasil diperbarui.`);

                            clearSiteForm();

                            displaySites();

                            resetSiteFormForAdd();

                            showMessageBox('Site berhasil diperbarui!');

                        };

                        updateRequest.onerror = (event) => {

                            console.error('Gagal memperbarui site:', event.target.errorCode);

                            showMessageBox('Error: Gagal memperbarui site. Mungkin nama site sudah ada.');

                        };

                    } else {

                        showMessageBox('Site tidak ditemukan untuk diperbarui.');

                    }

                };

                getRequest.onerror = (event) => {

                    console.error('Gagal mengambil site untuk diperbarui:', event.target.errorCode);

                };

            }



            function displaySites() {

                sitesTableBody.innerHTML = '';

                const transaction = db.transaction([STORE_SITES], 'readonly');

                const objectStore = transaction.objectStore(STORE_SITES);

                const request = objectStore.openCursor();

                request.onsuccess = (event) => {

                    const cursor = event.target.result;

                    if (cursor) {

                        const site = cursor.value;

                        const row = sitesTableBody.insertRow();

                        row.className = 'hover:bg-gray-50';

                        row.innerHTML = `

                            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${site.siteName}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${site.pic}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${site.address}</td>

                            <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">

                                <button data-id="${site.id}" class="edit-site-btn bg-yellow-400 hover:bg-yellow-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out mr-2">Edit</button>

                                <button data-id="${site.id}" class="delete-site-btn bg-red-400 hover:bg-red-500 text-white font-medium py-2 px-4 rounded-lg transition duration-300 ease-in-out">Hapus</button>

                            </td>

                        `;

                        row.querySelector('.edit-site-btn').addEventListener('click', () => populateSiteFormForEdit(site.id));

                        row.querySelector('.delete-site-btn').addEventListener('click', () => deleteSite(site.id));

                        cursor.continue();

                    } else {

                        console.log('Semua site telah ditampilkan.');

                    }

                };

                request.onerror = (event) => {

                    console.error('Gagal menampilkan site:', event.target.errorCode);

                };

            }



            function populateSiteFormForEdit(id) {

                const transaction = db.transaction([STORE_SITES], 'readonly');

                const objectStore = transaction.objectStore(STORE_SITES);

                const request = objectStore.get(id);

                request.onsuccess = (event) => {

                    const site = event.target.result;

                    if (site) {

                        siteNameInput.value = site.siteName;

                        sitePICInput.value = site.pic;

                        siteAddressInput.value = site.address;

                        editingSiteId = site.id;

                        saveSiteBtn.textContent = 'Perbarui Site';

                        saveSiteBtn.classList.remove('bg-blue-600', 'hover:bg-blue-700');

                        saveSiteBtn.classList.add('bg-green-600', 'hover:bg-green-700');

                        showMessageBox('Mode Edit: Isi form untuk memperbarui site.');

                    }

                };

            }



            function resetSiteFormForAdd() {

                clearSiteForm();

                editingSiteId = null;

                saveSiteBtn.textContent = 'Simpan Site';

                saveSiteBtn.classList.remove('bg-green-600', 'hover:bg-green-700');

                saveSiteBtn.classList.add('bg-blue-600', 'hover:bg-blue-700');

            }



            function deleteSite(id) {

                if (!confirm('Apakah kamu yakin ingin menghapus site ini?')) {

                    return;

                }

                const transaction = db.transaction([STORE_SITES], 'readwrite');

                const objectStore = transaction.objectStore(STORE_SITES);

                const request = objectStore.delete(id);

                request.onsuccess = () => {

                    console.log(`Site dengan ID ${id} berhasil dihapus.`);

                    displaySites();

                    showMessageBox('Site berhasil dihapus!');

                };

                request.onerror = (event) => {

                    console.error('Gagal menghapus site:', event.target.errorCode);

                    showMessageBox('Error: Gagal menghapus site.');

                };

            }



            function clearSiteForm() {

                siteNameInput.value = '';

                sitePICInput.value = '';

                siteAddressInput.value = '';

            }



            function backupData() {

                const transaction = db.transaction([STORE_INVENTORY_ITEMS, STORE_EXTERNAL_RECEIPTS, STORE_EXTERNAL_PURCHASES, STORE_EXTERNAL_SHIPMENTS, STORE_OTHER_EXTERNAL_TRANSACTIONS, STORE_OTHER_INTERNAL_TRANSACTIONS, STORE_SUPPLIERS, STORE_USERS, STORE_SITES], 'readonly');

                const data = {};

                const stores = [STORE_INVENTORY_ITEMS, STORE_EXTERNAL_RECEIPTS, STORE_EXTERNAL_PURCHASES, STORE_EXTERNAL_SHIPMENTS, STORE_OTHER_EXTERNAL_TRANSACTIONS, STORE_OTHER_INTERNAL_TRANSACTIONS, STORE_SUPPLIERS, STORE_USERS, STORE_SITES];



                let completed = 0;

                stores.forEach(storeName => {

                    const objectStore = transaction.objectStore(storeName);

                    const request = objectStore.getAll();

                    request.onsuccess = (event) => {

                        data[storeName] = event.target.result;

                        completed++;

                        if (completed === stores.length) {

                            const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });

                            const url = URL.createObjectURL(blob);

                            const a = document.createElement('a');

                            a.href = url;

                            a.download = `gudang_data_backup_${new Date().toISOString().slice(0,10)}.json`;

                            document.body.appendChild(a);

                            a.click();

                            document.body.removeChild(a);

                            URL.revokeObjectURL(url);

                            showMessageBox('Backup data berhasil diekspor!');

                        }

                    };

                    request.onerror = (event) => {

                        console.error('Gagal membaca data dari store:', storeName, event.target.errorCode);

                        showMessageBox(`Error: Gagal backup data dari ${storeName}.`);

                    };

                });

            }



            function restoreData() {

                if (!restoreFileInput.files.length) {

                    showMessageBox('Pilih file backup untuk diimpor.');

                    return;

                }

                if (!confirm('PERINGATAN: Mengimpor data akan menimpa semua data yang ada. Lanjutkan?')) {

                    return;

                }



                const file = restoreFileInput.files[0];

                const reader = new FileReader();



                reader.onload = (event) => {

                    try {

                        const importedData = JSON.parse(event.target.result);

                        const transaction = db.transaction([STORE_INVENTORY_ITEMS, STORE_EXTERNAL_RECEIPTS, STORE_EXTERNAL_PURCHASES, STORE_EXTERNAL_SHIPMENTS, STORE_OTHER_EXTERNAL_TRANSACTIONS, STORE_OTHER_INTERNAL_TRANSACTIONS, STORE_SUPPLIERS, STORE_USERS, STORE_SITES], 'readwrite');

                        let completed = 0;

                        const stores = [STORE_INVENTORY_ITEMS, STORE_EXTERNAL_RECEIPTS, STORE_EXTERNAL_PURCHASES, STORE_EXTERNAL_SHIPMENTS, STORE_OTHER_EXTERNAL_TRANSACTIONS, STORE_OTHER_INTERNAL_TRANSACTIONS, STORE_SUPPLIERS, STORE_USERS, STORE_SITES];



                        stores.forEach(storeName => {

                            const objectStore = transaction.objectStore(storeName);

                            objectStore.clear().onsuccess = () => {

                                if (importedData[storeName]) {

                                    importedData[storeName].forEach(item => {

                                        objectStore.add(item);

                                    });

                                }

                                completed++;

                                if (completed === stores.length) {

                                    transaction.oncomplete = () => {

                                        showMessageBox('Data berhasil diimpor dan diperbarui!');

                                        displayItems();

                                        displayReceipts();

                                        displayPurchases();

                                        displayShipments();

                                        displayOtherExternalTransactions();

                                        displayOtherInternalTransactions();

                                        displaySuppliers();

                                        displayUsers();

                                        displaySites();

                                    };

                                    transaction.onerror = (event) => {

                                        console.error('Gagal menulis data saat restore:', event.target.errorCode);

                                        showMessageBox('Error: Gagal menulis data saat restore.');

                                    };

                                }

                            };

                            objectStore.clear().onerror = (event) => {

                                console.error('Gagal membersihkan store saat restore:', storeName, event.target.errorCode);

                                showMessageBox(`Error: Gagal membersihkan store ${storeName} saat restore.`);

                            };

                        });

                    } catch (e) {

                        console.error('Gagal memparsing file JSON:', e);

                        showMessageBox('Error: File bukan format JSON yang valid.');

                    }

                };

                reader.onerror = (event) => {

                    console.error('Gagal membaca file:', event.target.errorCode);

                    showMessageBox('Error: Gagal membaca file.');

                };

                reader.readAsText(file);

            }

// --- Fungsi Laporan ---
async function generateGlobalReport() {
                const globalReportOutput = document.getElementById('tab-global-report').querySelector('div');
                globalReportOutput.innerHTML = '<p class="text-gray-500">Memuat laporan global dengan detail item...</p>';

                const inventorySummary = {}; // Kunci: `${itemName}|${itemSpecSize}`, Nilai: { category, name, specSize, unit, masuk, keluar, pembelian, kerusakan, kehilangan, balance }

                // Helper untuk mengambil semua data dari object store
                const getAllData = (storeName) => {
                    return new Promise((resolve, reject) => {
                        const transaction = db.transaction([storeName], 'readonly');
                        const objectStore = transaction.objectStore(storeName);
                        const request = objectStore.getAll();
                        request.onsuccess = (event) => resolve(event.target.result);
                        request.onerror = (event) => {
                            console.error(`Gagal membaca data dari ${storeName}:`, event.target.errorCode);
                            reject(`Gagal membaca data dari ${storeName}`);
                        };
                    });
                };

                try {
                    const inventoryItems = await getAllData(STORE_INVENTORY_ITEMS);
                    const receipts = await getAllData(STORE_EXTERNAL_RECEIPTS);
                    const purchases = await getAllData(STORE_EXTERNAL_PURCHASES);
                    const shipments = await getAllData(STORE_EXTERNAL_SHIPMENTS);
                    const otherExternalTransactions = await getAllData(STORE_OTHER_EXTERNAL_TRANSACTIONS);
                    const otherInternalTransactions = await getAllData(STORE_OTHER_INTERNAL_TRANSACTIONS);

                    // Inisialisasi ringkasan inventaris dari master item
                    inventoryItems.forEach(item => {
                        const key = `${item.itemName}|${item.itemSpecSize}`;
                        inventorySummary[key] = {
                            no: 0, // Akan diisi nanti saat iterasi
                            itemCategory: item.itemCategory,
                            itemName: item.itemName,
                            itemSpecSize: item.itemSpecSize,
                            itemUnit: item.itemUnit,
                            masuk: 0,
                            keluar: 0,
                            pembelian: 0,
                            kerusakan: 0,
                            kehilangan: 0,
                            balance: 0, // Ini akan menjadi stok akhir (masuk - keluar)
                            originalItem: item // Simpan referensi ke item asli jika perlu detail lebih lanjut
                        };
                    });

                    // Proses Penerimaan (Masuk)
                    receipts.forEach(receipt => {
                        receipt.items.forEach(item => {
                            const key = `${item.itemName}|${item.specSize || 'N/A'}`; // Gunakan specSize dari item jika ada, kalau tidak N/A
                            if (inventorySummary[key]) {
                                inventorySummary[key].masuk += item.quantity;
                            } else {
                                // Jika ada item di transaksi tapi tidak ada di master item, tambahkan sebagai "unknown"
                                inventorySummary[key] = {
                                    no: 0,
                                    itemCategory: 'Unknown',
                                    itemName: item.itemName,
                                    itemSpecSize: item.specSize || 'N/A',
                                    itemUnit: item.unit || 'Pcs', // Asumsi default unit
                                    masuk: item.quantity,
                                    keluar: 0,
                                    pembelian: 0,
                                    kerusakan: 0,
                                    kehilangan: 0,
                                    balance: 0,
                                    originalItem: null
                                };
                            }
                        });
                    });

                    // Proses Pembelian (Masuk)
                    purchases.forEach(purchase => {
                        purchase.items.forEach(item => {
                            const key = `${item.itemName}|${item.specSize || 'N/A'}`;
                             if (inventorySummary[key]) {
                                inventorySummary[key].pembelian += item.quantity;
                                inventorySummary[key].masuk += item.quantity; // Pembelian juga berarti masuk
                            } else {
                                // Tambahkan jika item tidak ada di master inventory
                                inventorySummary[key] = {
                                    no: 0,
                                    itemCategory: 'Unknown',
                                    itemName: item.itemName,
                                    itemSpecSize: item.specSize || 'N/A',
                                    itemUnit: item.unit || 'Pcs',
                                    masuk: item.quantity,
                                    keluar: 0,
                                    pembelian: item.quantity,
                                    kerusakan: 0,
                                    kehilangan: 0,
                                    balance: 0,
                                    originalItem: null
                                };
                            }
                        });
                    });

                    // Proses Pengiriman (Keluar)
                    shipments.forEach(shipment => {
                        shipment.items.forEach(item => {
                            const key = `${item.itemName}|${item.specSize || 'N/A'}`;
                            if (inventorySummary[key]) {
                                inventorySummary[key].keluar += item.quantity;
                            }
                        });
                    });

                    // Proses Transaksi Lain Eksternal (Kerusakan, Kehilangan, Lain-lain)
                    otherExternalTransactions.forEach(transaction => {
                        transaction.items.forEach(item => {
                            const key = `${item.itemName}|${item.specSize || 'N/A'}`;
                            if (inventorySummary[key]) {
                                if (transaction.transactionType === 'kerusakan') {
                                    inventorySummary[key].kerusakan += item.quantity;
                                    inventorySummary[key].keluar += item.quantity; // Kerusakan juga berarti keluar
                                } else if (transaction.transactionType === 'kehilangan') {
                                    inventorySummary[key].kehilangan += item.quantity;
                                    inventorySummary[key].keluar += item.quantity; // Kehilangan juga berarti keluar
                                } else {
                                    // Jenis transaksi lain eksternal yang mengurangi stok bisa ditambahkan di sini
                                    // Untuk sementara, kita anggap "lain-lain" juga mengurangi stok
                                    inventorySummary[key].kelkeluar += item.quantity;
                                }
                            }
                        });
                    });

                    // Proses Transaksi Lain Internal (Kerusakan, Kehilangan, Lain-lain)
                    otherInternalTransactions.forEach(transaction => {
                        transaction.items.forEach(item => {
                            const key = `${item.itemName}|${item.specSize || 'N/A'}`;
                            if (inventorySummary[key]) {
                                if (transaction.transactionType === 'kerusakan') {
                                    inventorySummary[key].kerusakan += item.quantity;
                                    inventorySummary[key].keluar += item.quantity; // Kerusakan juga berarti keluar
                                } else if (transaction.transactionType === 'kehilangan') {
                                    inventorySummary[key].kehilangan += item.quantity;
                                    inventorySummary[key].keluar += item.quantity; // Kehilangan juga berarti keluar
                                } else {
                                    // Jenis transaksi lain internal yang mengurangi stok bisa ditambahkan di sini
                                     inventorySummary[key].keluar += item.quantity;
                                }
                            }
                        });
                    });


                    // Hitung balance dan siapkan data untuk tabel
                    const reportData = Object.values(inventorySummary).map((item, index) => {
                        item.no = index + 1;
                        item.balance = item.masuk - item.keluar; // Hitung balance
                        return item;
                    }).sort((a, b) => a.itemName.localeCompare(b.itemName)); // Urutkan berdasarkan nama barang

                    if (reportData.length === 0) {
                        globalReportOutput.innerHTML = '<p class="text-gray-600">Tidak ada data item yang tersedia untuk laporan global.</p>';
                        return;
                    }

                    let reportHtml = `
                        <h4 class="font-bold text-lg mb-4">Ringkasan Stok Global Per Item:</h4>
                        <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">
                            <table class="min-w-full divide-y divide-gray-200">
                                <thead class="bg-gray-100">
                                    <tr>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">No</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Spec/Size</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Unit</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Masuk</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Keluar</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Pembelian</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Kerusakan</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Kehilangan</th>
                                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Balance</th>
                                    </tr>
                                </thead>
                                <tbody class="bg-white divide-y divide-gray-200">
                    `;

                    reportData.forEach(item => {
                        reportHtml += `
                            <tr class="hover:bg-gray-50">
                                <td class="px-4 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.no}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-gray-900">${item.itemName}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-gray-500">${item.itemSpecSize || '-'}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-gray-500">${item.itemUnit || '-'}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-green-600 font-semibold">${item.masuk}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-red-600 font-semibold">${item.keluar}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-blue-600">${item.pembelian}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-orange-600">${item.kerusakan}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm text-purple-600">${item.kehilangan}</td>
                                <td class="px-4 py-4 whitespace-nowrap text-sm font-bold ${item.balance >= 0 ? 'text-gray-900' : 'text-red-700'}">${item.balance}</td>
                            </tr>
                        `;
                    });

                    reportHtml += `
                                </tbody>
                            </table>
                        </div>
                    `;
                    globalReportOutput.innerHTML = reportHtml;

                } catch (error) {
                    console.error('Error generating global report:', error);
                    globalReportOutput.innerHTML = '<p class="text-red-500">Gagal memuat laporan global.</p>';
                    showMessageBox('Error: Gagal memuat laporan global.');
                }
            }
            


            async function generateUserReport() {
                const selectedUser = reportUserSelect.value;
                userReportOutput.innerHTML = ''; // Clear previous report

                if (!selectedUser) {
                    showMessageBox('Pilih user untuk menampilkan laporan.');
                    return;
                }

                userReportOutput.innerHTML = `<p class="text-gray-500">Memuat laporan untuk ${selectedUser}...</p>`;

                let userTransactions = [];

                try {
                    // Fetch Other Internal Transactions related to the user
                    const oitTransaction = db.transaction([STORE_OTHER_INTERNAL_TRANSACTIONS], 'readonly');
                    const oitStore = oitTransaction.objectStore(STORE_OTHER_INTERNAL_TRANSACTIONS);
                    const oitRequest = oitStore.openCursor();

                    await new Promise(resolve => {
                        oitRequest.onsuccess = (event) => {
                            const cursor = event.target.result;
                            if (cursor) {
                                const transaction = cursor.value;
                                // Check if the user is involved in this internal transaction (e.g., as partyName)
                                if (transaction.partyName === selectedUser) {
                                    userTransactions.push({
                                        type: 'Internal',
                                        date: transaction.otherInternalDate,
                                        docNum: transaction.documentNumber,
                                        transactionType: transaction.transactionType,
                                        items: transaction.items,
                                        notes: `Pihak Terkait: ${transaction.partyName}`
                                    });
                                }
                                cursor.continue();
                            } else {
                                resolve();
                            }
                        };
                        oitRequest.onerror = (event) => {
                            console.error('Error fetching internal transactions for user report:', event.target.errorCode);
                            showMessageBox('Error: Gagal memuat data transaksi internal.');
                            resolve(); // Resolve to not block the process
                        };
                    });

                    if (userTransactions.length === 0) {
                        userReportOutput.innerHTML = `<p class="text-gray-600">Tidak ada transaksi yang tercatat untuk user <strong>${selectedUser}</strong>.</p>`;
                        return;
                    }

                    let reportHtml = `<h4 class="font-bold text-lg mb-4">Laporan Transaksi untuk User: <span class="text-blue-600">${selectedUser}</span></h4>`;
                    
                    userTransactions.sort((a, b) => new Date(b.date) - new Date(a.date)); // Sort by date, newest first

                    userTransactions.forEach(trans => {
                        reportHtml += `
                            <div class="border border-gray-200 rounded-lg p-4 mb-4 bg-white shadow-sm">
                                <p class="text-sm text-gray-500">Tanggal: <span class="font-semibold">${trans.date}</span> | Dokumen: <span class="font-semibold">${trans.docNum}</span> | Tipe: <span class="font-semibold">${trans.transactionType} (Internal)</span></p>
                                <ul class="list-disc pl-5 mt-2 text-gray-700">
                                    ${trans.items.map(item => `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`).join('')}
                                </ul>
                            </div>
                        `;
                    });

                    userReportOutput.innerHTML = reportHtml;

                } catch (error) {
                    console.error('Error generating user report:', error);
                    userReportOutput.innerHTML = '<p class="text-red-500">Gagal memuat laporan per user.</p>';
                    showMessageBox('Error: Gagal memuat laporan per user.');
                }
            }


            async function generateSiteReport() {
                const selectedSite = reportSiteSelect.value;
                siteReportOutput.innerHTML = ''; // Clear previous report

                if (!selectedSite) {
                    showMessageBox('Pilih site untuk menampilkan laporan.');
                    return;
                }

                siteReportOutput.innerHTML = `<p class="text-gray-500">Memuat laporan untuk ${selectedSite}...</p>`;

                let siteItems = {}; // { itemName: { brand: { qty: X, ... } } }

                try {
                    // Fetch External Receipts for this site
                    const receiptsTransaction = db.transaction([STORE_EXTERNAL_RECEIPTS], 'readonly');
                    const receiptsStore = receiptsTransaction.objectStore(STORE_EXTERNAL_RECEIPTS);
                    const receiptsRequest = receiptsStore.openCursor();

                    await new Promise(resolve => {
                        receiptsRequest.onsuccess = (event) => {
                            const cursor = event.target.result;
                            if (cursor) {
                                const receipt = cursor.value;
                                if (receipt.siteName === selectedSite) {
                                    receipt.items.forEach(item => {
                                        const key = `${item.itemName}-${item.brand || '-'}-${item.itemCode || '-'}-${item.serialNumber || '-'}-${item.assetNumber || '-'}`;
                                        if (!siteItems[key]) {
                                            siteItems[key] = { ...item, totalQuantity: 0 };
                                        }
                                        siteItems[key].totalQuantity += item.quantity;
                                    });
                                }
                                cursor.continue();
                            } else {
                                resolve();
                            }
                        };
                        receiptsRequest.onerror = (event) => {
                            console.error('Error fetching receipts for site report:', event.target.errorCode);
                            showMessageBox('Error: Gagal memuat data penerimaan.');
                            resolve();
                        };
                    });

                    // Fetch External Shipments from/to this site
                    const shipmentsTransaction = db.transaction([STORE_EXTERNAL_SHIPMENTS], 'readonly');
                    const shipmentsStore = shipmentsTransaction.objectStore(STORE_EXTERNAL_SHIPMENTS);
                    const shipmentsRequest = shipmentsStore.openCursor();

                    await new Promise(resolve => {
                        shipmentsRequest.onsuccess = (event) => {
                            const cursor = event.target.result;
                            if (cursor) {
                                const shipment = cursor.value;
                                if (shipment.destinationSite === selectedSite) { // Items arriving at this site
                                     shipment.items.forEach(item => {
                                        const key = `${item.itemName}-${item.brand || '-'}-${item.itemCode || '-'}-${item.serialNumber || '-'}-${item.assetNumber || '-'}`;
                                        if (!siteItems[key]) {
                                            siteItems[key] = { ...item, totalQuantity: 0 };
                                        }
                                        siteItems[key].totalQuantity += item.quantity; // Add to inventory
                                    });
                                }
                                // If you also want to track items *leaving* the site, you'd need a "sourceSite" field
                                // For now, we'll assume "receipts" and "shipments.destinationSite" cover incoming.
                                cursor.continue();
                            } else {
                                resolve();
                            }
                        };
                        shipmentsRequest.onerror = (event) => {
                            console.error('Error fetching shipments for site report:', event.target.errorCode);
                            showMessageBox('Error: Gagal memuat data pengiriman.');
                            resolve();
                        };
                    });

                    const itemsArray = Object.values(siteItems);
                    if (itemsArray.length === 0) {
                        siteReportOutput.innerHTML = `<p class="text-gray-600">Tidak ada barang yang tercatat untuk site <strong>${selectedSite}</strong>.</p>`;
                        return;
                    }

                    let reportHtml = `<h4 class="font-bold text-lg mb-4">Laporan Inventaris untuk Site: <span class="text-blue-600">${selectedSite}</span></h4>`;
                    reportHtml += `
                        <div class="overflow-x-auto bg-gray-50 rounded-lg shadow-sm">
                            <table class="min-w-full divide-y divide-gray-200">
                                <thead class="bg-gray-100">
                                    <tr>
                                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nama Barang</th>
                                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Brand</th>
                                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Kode Barang</th>
                                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Serial Number</th>
                                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nomor Asset</th>
                                        <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Total Qty</th>
                                    </tr>
                                </thead>
                                <tbody class="bg-white divide-y divide-gray-200">
                    `;

                    itemsArray.sort((a, b) => a.itemName.localeCompare(b.itemName)); // Sort by item name

                    itemsArray.forEach(item => {
                        reportHtml += `
                            <tr class="hover:bg-gray-50">
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${item.itemName}</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.brand || '-'}</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.itemCode || '-'}</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.serialNumber || '-'}</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${item.assetNumber || '-'}</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900 font-bold">${item.totalQuantity}</td>
                            </tr>
                        `;
                    });

                    reportHtml += `
                                </tbody>
                            </table>
                        </div>
                    `;
                    siteReportOutput.innerHTML = reportHtml;

                } catch (error) {
                    console.error('Error generating site report:', error);
                    siteReportOutput.innerHTML = '<p class="text-red-500">Gagal memuat laporan per site.</p>';
                    showMessageBox('Error: Gagal memuat laporan per site.');
                }
            }


            async function generateSupplierReport() {
                const selectedSupplier = reportSupplierSelect.value;
                supplierReportOutput.innerHTML = ''; // Clear previous report

                if (!selectedSupplier) {
                    showMessageBox('Pilih supplier untuk menampilkan laporan.');
                    return;
                }

                supplierReportOutput.innerHTML = `<p class="text-gray-500">Memuat laporan untuk ${selectedSupplier}...</p>`;

                let supplierReceipts = [];
                let supplierPurchases = [];

                try {
                    // Fetch External Receipts from this supplier
                    const receiptsTransaction = db.transaction([STORE_EXTERNAL_RECEIPTS], 'readonly');
                    const receiptsStore = receiptsTransaction.objectStore(STORE_EXTERNAL_RECEIPTS);
                    const receiptsRequest = receiptsStore.openCursor();

                    await new Promise(resolve => {
                        receiptsRequest.onsuccess = (event) => {
                            const cursor = event.target.result;
                            if (cursor) {
                                const receipt = cursor.value;
                                // Assuming 'siteName' in receipts can also represent the supplier if it's external,
                                // or you might need a dedicated 'supplierName' field in STORE_EXTERNAL_RECEIPTS
                                if (receipt.siteName === selectedSupplier) { // This might need adjustment based on your data structure for receipts from suppliers
                                    supplierReceipts.push(receipt);
                                }
                                cursor.continue();
                            } else {
                                resolve();
                            }
                        };
                        receiptsRequest.onerror = (event) => {
                            console.error('Error fetching receipts for supplier report:', event.target.errorCode);
                            showMessageBox('Error: Gagal memuat data penerimaan.');
                            resolve();
                        };
                    });

                    // Fetch External Purchases from this supplier
                    const purchasesTransaction = db.transaction([STORE_EXTERNAL_PURCHASES], 'readonly');
                    const purchasesStore = purchasesTransaction.objectStore(STORE_EXTERNAL_PURCHASES);
                    const purchasesRequest = purchasesStore.openCursor();

                    await new Promise(resolve => {
                        purchasesRequest.onsuccess = (event) => {
                            const cursor = event.target.result;
                            if (cursor) {
                                const purchase = cursor.value;
                                if (purchase.supplierName === selectedSupplier) {
                                    supplierPurchases.push(purchase);
                                }
                                cursor.continue();
                            } else {
                                resolve();
                            }
                        };
                        purchasesRequest.onerror = (event) => {
                            console.error('Error fetching purchases for supplier report:', event.target.errorCode);
                            showMessageBox('Error: Gagal memuat data pembelian.');
                            resolve();
                        };
                    });

                    if (supplierReceipts.length === 0 && supplierPurchases.length === 0) {
                        supplierReportOutput.innerHTML = `<p class="text-gray-600">Tidak ada transaksi yang tercatat untuk supplier <strong>${selectedSupplier}</strong>.</p>`;
                        return;
                    }

                    let reportHtml = `<h4 class="font-bold text-lg mb-4">Laporan Transaksi untuk Supplier: <span class="text-blue-600">${selectedSupplier}</span></h4>`;

                    // Display Purchases
                    if (supplierPurchases.length > 0) {
                        reportHtml += `<h5 class="font-bold text-md mt-6 mb-2">Daftar Pembelian:</h5>`;
                        supplierPurchases.sort((a, b) => new Date(b.purchaseDate) - new Date(a.purchaseDate));
                        supplierPurchases.forEach(purchase => {
                            reportHtml += `
                                <div class="border border-gray-200 rounded-lg p-4 mb-4 bg-white shadow-sm">
                                    <p class="text-sm text-gray-500">Tanggal: <span class="font-semibold">${purchase.purchaseDate}</span> | Dokumen: <span class="font-semibold">${purchase.documentNumber}</span></p>
                                    <ul class="list-disc pl-5 mt-2 text-gray-700">
                                        ${purchase.items.map(item => `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`).join('')}
                                    </ul>
                                </div>
                            `;
                        });
                    }

                    // Display Receipts (if 'siteName' for receipts represents supplier)
                    if (supplierReceipts.length > 0) {
                         reportHtml += `<h5 class="font-bold text-md ${supplierPurchases.length > 0 ? 'mt-6' : 'mt-0'} mb-2">Daftar Penerimaan (jika Site = Supplier):</h5>`;
                        supplierReceipts.sort((a, b) => new Date(b.receiptDate) - new Date(a.receiptDate));
                        supplierReceipts.forEach(receipt => {
                            reportHtml += `
                                <div class="border border-gray-200 rounded-lg p-4 mb-4 bg-white shadow-sm">
                                    <p class="text-sm text-gray-500">Tanggal: <span class="font-semibold">${receipt.receiptDate}</span> | Dokumen: <span class="font-semibold">${receipt.documentNumber}</span></p>
                                    <ul class="list-disc pl-5 mt-2 text-gray-700">
                                        ${receipt.items.map(item => `<li>${item.itemName} (${item.brand || '-'}) - ${item.quantity} ${item.notes ? `(${item.notes})` : ''}</li>`).join('')}
                                    </ul>
                                </div>
                            `;
                        });
                    }

                    supplierReportOutput.innerHTML = reportHtml;

                } catch (error) {
                    console.error('Error generating supplier report:', error);
                    supplierReportOutput.innerHTML = '<p class="text-red-500">Gagal memuat laporan per supplier.</p>';
                    showMessageBox('Error: Gagal memuat laporan per supplier.');
                }
            }

            // PENTING: Tambahkan event listener untuk tombol "Tampilkan Laporan"
            generateUserReportBtn.addEventListener('click', generateUserReport);
            generateSiteReportBtn.addEventListener('click', generateSiteReport);
            generateSupplierReportBtn.addEventListener('click', generateSupplierReport);

            // Tambahkan event listener untuk tab "Laporan" itu sendiri agar Global Report tampil pertama
            // Saat tab "Laporan" di sidebar diklik, kita ingin tab "Global" aktif dan laporan global tampil
            navLaporan.addEventListener('click', (e) => {
                e.preventDefault();
                showSection('section-laporan');
                // Secara otomatis klik tombol tab "Global" untuk memicu laporan awal
                document.querySelector('#section-laporan button[data-tab="global-report"]').click();
                generateGlobalReport(); // Panggil fungsi laporan global saat tab laporan aktif
            });

            saveItemBtn.addEventListener('click', () => {

                const category = itemCategoryInput.value;

                const name = itemNameInput.value;

                const specSize = itemSpecSizeInput.value;

                const unit = itemUnitInput.value;

                if (editingItemId !== null) {

                    updateItem(editingItemId, category, name, specSize, unit);

                } else {

                    addItem(category, name, specSize, unit);

                }

            });

            cancelEditBtn.addEventListener('click', resetFormForAdd);

            clearAllItemsBtn.addEventListener('click', clearAllItems);



            addCurrentReceiptItemToListBtn.addEventListener('click', addCurrentReceiptItemToList);

            cancelEditCurrentReceiptItemBtn.addEventListener('click', () => {

                clearCurrentReceiptItemInputs();

                editingCurrentReceiptItemIndex = null;

                addCurrentReceiptItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentReceiptItemBtn.classList.add('hidden');

            });

            saveReceiptBtn.addEventListener('click', saveReceiptTransaction);



            addCurrentPurchaseItemToListBtn.addEventListener('click', addCurrentPurchaseItemToList);

            cancelEditCurrentPurchaseItemBtn.addEventListener('click', () => {

                clearCurrentPurchaseItemInputs();

                editingCurrentPurchaseItemIndex = null;

                addCurrentPurchaseItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentPurchaseItemBtn.classList.add('hidden');

            });

            savePurchaseBtn.addEventListener('click', savePurchaseTransaction);



            addCurrentShipmentItemToListBtn.addEventListener('click', addCurrentShipmentItemToList);

            cancelEditCurrentShipmentItemBtn.addEventListener('click', () => {

                clearCurrentShipmentItemInputs();

                editingCurrentShipmentItemIndex = null;

                addCurrentShipmentItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentShipmentItemBtn.classList.add('hidden');

            });

            saveShipmentBtn.addEventListener('click', saveShipmentTransaction);



            addCurrentOtherExternalItemToListBtn.addEventListener('click', addCurrentOtherExternalItemToList);

            cancelEditCurrentOtherExternalItemBtn.addEventListener('click', () => {

                clearCurrentOtherExternalItemInputs();

                editingCurrentOtherExternalItemIndex = null;

                addCurrentOtherExternalItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentOtherExternalItemBtn.classList.add('hidden');

            });

            saveOtherExternalTransactionBtn.addEventListener('click', saveOtherExternalTransaction);



            addCurrentOtherInternalItemToListBtn.addEventListener('click', addCurrentOtherInternalItemToList);

            cancelEditCurrentOtherInternalItemBtn.addEventListener('click', () => {

                clearCurrentOtherInternalItemInputs();

                editingCurrentOtherInternalItemIndex = null;

                addCurrentOtherInternalItemToListBtn.textContent = 'Tambah ke Daftar';

                cancelEditCurrentOtherInternalItemBtn.classList.add('hidden');

            });

            saveOtherInternalTransactionBtn.addEventListener('click', saveOtherInternalTransaction);



            saveSupplierBtn.addEventListener('click', () => {

                if (editingSupplierId !== null) {

                    updateSupplier(editingSupplierId, supplierNameInput.value, supplierContactInput.value, supplierAddressInput.value);

                } else {

                    addSupplier();

                }

            });



            addMemberNameBtn.addEventListener('click', () => addMemberNameHandler());

            saveUserBtn.addEventListener('click', () => {

                if (editingUserId !== null) {

                    updateUser(editingUserId, userNameInput.value, userSectionInput.value, userStatusInput.value, getUserMemberNames());

                } else {

                    addUser();

                }

            });



            saveSiteBtn.addEventListener('click', () => {

                if (editingSiteId !== null) {

                    updateSite(editingSiteId, siteNameInput.value, sitePICInput.value, siteAddressInput.value);

                } else {

                    addSite();

                }

            });



            navDashboard.addEventListener('click', (e) => { e.preventDefault(); showSection('section-dashboard'); });

            navManajemenItem.addEventListener('click', (e) => { e.preventDefault(); showSection('section-manajemen-item'); });

            navTransaksiEksternal.addEventListener('click', (e) => { e.preventDefault(); showSection('section-transaksi-eksternal'); });

            navTransaksiInternal.addEventListener('click', (e) => { e.preventDefault(); showSection('section-transaksi-internal'); });

            navPihakTerkait.addEventListener('click', (e) => {

                e.preventDefault();

                showSection('section-pihak-terkait');

                document.querySelector('#section-pihak-terkait button[data-tab="supplier"]').click();

            });

            navBackupRestore.addEventListener('click', (e) => { e.preventDefault(); showSection('section-backup-restore'); });

            navLaporan.addEventListener('click', (e) => { e.preventDefault(); showSection('section-laporan'); });

            navPengaturan.addEventListener('click', (e) => { e.preventDefault(); showSection('section-pengaturan'); });



            backupDataBtn.addEventListener('click', backupData);

            restoreDataBtn.addEventListener('click', restoreData);



           openDatabase().then(() => {
                setupTabs('section-transaksi-eksternal');
                setupTabs('section-transaksi-internal');
                setupTabs('section-pihak-terkait');
                // showSection('section-manajemen-item'); // Baris ini dipindahkan ke bawah

                // --- BAGIAN INI YANG PERLU DIUPDATE ---
                setupTabs('section-laporan'); // <-- TAMBAHKAN BARIS INI
                
                Promise.all([
                    loadAvailableItems(),
                    loadAvailableSuppliers(),
                    loadAvailableSites(),
                    loadAvailableUsers()
                ]).then(() => {
                    clearUserForm();
                    clearReceiptForm();
                    clearPurchaseForm();
                    clearShipmentForm();
                    clearOtherExternalForm();
                    clearOtherInternalForm();
                    
                    // Pindah ini ke dalam .then() Promise.all
                    // Ini memastikan dropdown terisi dan database siap sebelum section awal ditampilkan
                    showSection('section-manajemen-item'); // Pindahkan ke sini
                    document.querySelector('#section-laporan button[data-tab="global-report"]').click(); // Ini akan mengaktifkan tab Global
                    generateGlobalReport(); // Dan ini akan memicu laporan global
                });
            });

        });
  </script>
</body>
</html>
