<!doctype html>
<html lang="en" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AL AMEEN TRADERS - Modern Quotation System</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.31/jspdf.plugin.autotable.min.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;500;600;700&amp;family=Outfit:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; }
    html, body { height: 100%; width: 100%; }
    .font-heading { font-family: 'Outfit', sans-serif; letter-spacing: -0.5px; }
    .font-body { font-family: 'Sora', sans-serif; }
    
    .gradient-primary { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
    .gradient-accent { background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); }
    
    .animated-bg { position: relative; overflow: hidden; }
    .animated-bg::before {
      content: ''; position: absolute; top: -50%; right: -10%; width: 600px; height: 600px;
      background: rgba(102, 126, 234, 0.1); border-radius: 50%; animation: float 20s infinite ease-in-out;
    }
    .animated-bg::after {
      content: ''; position: absolute; bottom: -40%; left: -5%; width: 500px; height: 500px;
      background: rgba(118, 75, 162, 0.1); border-radius: 50%; animation: float 25s infinite ease-in-out reverse;
    }
    @keyframes float { 0%, 100% { transform: translate(0, 0); } 50% { transform: translate(30px, 30px); } }
    
    .toast { animation: toastSlide 0.4s cubic-bezier(0.34, 1.56, 0.64, 1), fadeOut 0.3s ease-in 2.7s forwards; }
    @keyframes toastSlide { from { transform: translateX(400px) scale(0.8); opacity: 0; } to { transform: translateX(0) scale(1); opacity: 1; } }
    @keyframes fadeOut { from { opacity: 1; } to { opacity: 0; } }
    
    .btn-primary { transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1); position: relative; overflow: hidden; }
    .btn-primary::before { content: ''; position: absolute; top: 0; left: -100%; width: 100%; height: 100%;
      background: rgba(255, 255, 255, 0.1); transition: left 0.3s ease; }
    .btn-primary:hover::before { left: 100%; }
    .btn-primary:hover { transform: translateY(-3px); box-shadow: 0 12px 32px rgba(102, 126, 234, 0.4); }
    
    .input-field { transition: all 0.3s ease; background: rgba(255, 255, 255, 0.6); border: 1px solid rgba(102, 126, 234, 0.2); }
    .input-field:focus { background: rgba(255, 255, 255, 0.95); border-color: #667eea; box-shadow: 0 0 0 4px rgba(102, 126, 234, 0.1); transform: translateY(-2px); }
    
    .card-modern { border-radius: 20px; border: 1px solid rgba(102, 126, 234, 0.1); box-shadow: 0 8px 24px rgba(102, 126, 234, 0.08);
      transition: all 0.3s ease; backdrop-filter: blur(10px); }
    .card-modern:hover { box-shadow: 0 16px 48px rgba(102, 126, 234, 0.15); transform: translateY(-4px); border-color: rgba(102, 126, 234, 0.2); }
    
    .table-row { transition: all 0.2s ease; border-bottom: 1px solid rgba(102, 126, 234, 0.08); }
    .table-row:hover { background: linear-gradient(90deg, rgba(102, 126, 234, 0.08) 0%, transparent 100%); }
    
    .badge-gradient { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; }
    
    .fade-in { animation: fadeIn 0.5s ease; }
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
  </style>
  <style>@view-transition { navigation: auto; }</style>
 </head>
 <body class="h-full font-body bg-gradient-to-br from-slate-50 via-purple-50 to-slate-50 text-slate-800">
  <div id="app" class="h-full w-full overflow-auto"><!-- Login Screen - Modern Design -->
   <div id="login-screen" class="min-h-full flex items-center justify-center p-4 animated-bg bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900 relative overflow-hidden">
    <div class="w-full max-w-md relative z-10">
     <div class="backdrop-blur-xl bg-white/10 border border-white/20 rounded-3xl p-8 shadow-2xl">
      <div class="text-center mb-8">
       <div class="w-20 h-20 mx-auto mb-6 bg-gradient-to-br from-cyan-400 via-purple-500 to-pink-500 rounded-2xl flex items-center justify-center shadow-2xl transform hover:scale-110 transition-transform duration-300">
        <svg class="w-12 h-12 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
        </svg>
       </div>
       <h1 class="font-heading text-3xl font-bold text-white">AL AMEEN TRADERS</h1>
       <p class="text-purple-200 mt-2 text-sm font-medium">Smart Quotation System 2026</p>
      </div>
      <form id="login-form" class="space-y-4" onsubmit="handleLogin(event)">
       <div class="group"><label class="block text-sm font-semibold text-purple-100 mb-2.5">Username</label>
        <div class="relative">
         <svg class="w-5 h-5 text-purple-300 absolute left-3.5 top-1/2 transform -translate-y-1/2" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
         </svg><input type="text" id="login-username" required class="input-field w-full px-4 py-3 pl-11 bg-white/5 border border-white/20 rounded-xl text-white placeholder-white/40 focus:outline-none focus:border-cyan-400 transition-all focus:bg-white/10" placeholder="Enter username">
        </div>
       </div>
       <div class="group"><label class="block text-sm font-semibold text-purple-100 mb-2.5">Password</label>
        <div class="relative">
         <svg class="w-5 h-5 text-purple-300 absolute left-3.5 top-1/2 transform -translate-y-1/2" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
         </svg><input type="password" id="login-password" required class="input-field w-full px-4 py-3 pl-11 bg-white/5 border border-white/20 rounded-xl text-white placeholder-white/40 focus:outline-none focus:border-cyan-400 transition-all focus:bg-white/10" placeholder="Enter password">
        </div>
       </div>
       <div class="group"><label class="block text-sm font-semibold text-purple-100 mb-2.5">Staff Name</label>
        <div class="relative">
         <svg class="w-5 h-5 text-purple-300 absolute left-3.5 top-1/2 transform -translate-y-1/2" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
         </svg><input type="text" id="login-staff-name" required class="input-field w-full px-4 py-3 pl-11 bg-white/5 border border-white/20 rounded-xl text-white placeholder-white/40 focus:outline-none focus:border-cyan-400 transition-all focus:bg-white/10" placeholder="Enter your full name">
        </div>
       </div>
       <div id="login-error" class="hidden text-red-200 text-sm bg-red-500/20 p-3.5 rounded-lg border border-red-500/30 backdrop-blur"></div><button type="submit" id="login-btn" class="btn-primary w-full py-3.5 mt-6 bg-gradient-to-r from-cyan-500 via-purple-500 to-pink-500 text-white rounded-xl font-semibold hover:shadow-2xl hover:shadow-purple-500/50 transition-all duration-300 transform hover:scale-105"> Sign In to Dashboard </button>
      </form>
     </div>
    </div>
   </div><!-- Main Dashboard -->
   <div id="dashboard" class="hidden min-h-full"><!-- Modern Header -->
    <header class="sticky top-0 z-40 backdrop-blur-xl bg-white/80 border-b border-white/20 shadow-sm">
     <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
       <div class="flex items-center gap-3">
        <div class="w-10 h-10 bg-gradient-to-br from-cyan-400 via-purple-500 to-pink-500 rounded-xl flex items-center justify-center">
         <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
         </svg>
        </div>
        <div>
         <h1 id="header-shop-name" class="font-heading font-bold text-slate-800">AL AMEEN TRADERS</h1>
         <p class="text-xs text-purple-600 font-medium">Modern Quotation System</p>
        </div>
       </div>
       <div class="flex items-center gap-3"><span id="user-email" class="hidden sm:block text-sm text-slate-600"></span> <span id="staff-name-display" class="hidden sm:block text-sm font-semibold text-white px-3 py-1.5 bg-gradient-to-r from-purple-500 to-pink-500 rounded-lg"></span> <button id="logout-btn" class="px-4 py-2 text-slate-600 hover:text-slate-800 hover:bg-slate-100/50 rounded-lg transition-all text-sm font-medium">Sign Out</button>
       </div>
      </div>
     </div>
    </header><!-- Main Content -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8"><!-- Quotation Header Card -->
     <div class="card-modern p-8 mb-8 bg-white/60">
      <div class="flex flex-col lg:flex-row lg:items-start gap-8"><!-- Logo Upload -->
       <div class="flex-shrink-0"><label class="block text-sm font-semibold bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent mb-3">Business Logo</label>
        <div id="logo-preview" class="w-32 h-24 border-2 border-dashed border-purple-300 rounded-2xl flex items-center justify-center cursor-pointer hover:border-purple-500 transition-all bg-gradient-to-br from-purple-50 to-pink-50 overflow-hidden group">
         <div id="logo-placeholder" class="text-center group-hover:scale-110 transition-transform">
          <svg class="w-8 h-8 mx-auto text-purple-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" />
          </svg><span class="text-xs text-purple-400 mt-1 block">Upload Logo</span>
         </div><img id="logo-image" class="hidden h-full w-full object-contain" alt="Business Logo">
        </div><input type="file" id="logo-upload" accept="image/*" class="hidden">
       </div><!-- Business Info -->
       <div class="flex-grow">
        <div class="text-center lg:text-left mb-6">
         <h2 class="font-heading text-4xl font-bold bg-gradient-to-r from-purple-600 via-pink-600 to-purple-600 bg-clip-text text-transparent tracking-tight">QUOTATION</h2>
        </div>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
         <div>
          <p id="display-shop-name" class="font-semibold text-lg text-slate-800">AL AMEEN TRADERS</p>
          <p id="display-contact" class="text-slate-600 text-sm mt-2">📞 011 2731769</p>
          <p id="display-address" class="text-slate-600 text-sm">📍 201/1, Galle Road, Dehiwala</p>
         </div>
         <div class="sm:text-right space-y-3">
          <div><label class="block text-xs font-semibold text-purple-600 uppercase mb-2">Quotation No.</label> <input type="text" id="quotation-number" class="input-field w-full sm:w-48 px-4 py-2.5 border border-purple-200 rounded-xl focus:outline-none focus:border-purple-500 font-mono text-right" placeholder="QT-001">
          </div>
          <div><label class="block text-xs font-semibold text-purple-600 uppercase mb-2">Date</label> <input type="date" id="quotation-date" class="input-field w-full sm:w-48 px-4 py-2.5 border border-purple-200 rounded-xl focus:outline-none focus:border-purple-500 text-right">
          </div>
         </div>
        </div>
       </div>
      </div><!-- Customer Details -->
      <div class="mt-8 pt-8 border-t border-purple-100">
       <h3 class="text-sm font-semibold bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent mb-4">Customer Details</h3>
       <div class="grid grid-cols-1 sm:grid-cols-3 gap-4"><input type="text" id="customer-name" placeholder="Customer Name" class="input-field px-4 py-3 border border-purple-200 rounded-xl focus:outline-none focus:border-purple-500"> <input type="email" id="customer-email" placeholder="Customer Email" class="input-field px-4 py-3 border border-purple-200 rounded-xl focus:outline-none focus:border-purple-500">
        <div><label class="block text-xs font-semibold text-purple-600 uppercase mb-2">Staff Name</label> <input type="text" id="staff-name" readonly class="w-full px-4 py-3 border border-purple-200 rounded-xl bg-purple-50 text-slate-600 font-medium">
        </div>
       </div>
      </div>
     </div><!-- Items Table -->
     <div class="card-modern overflow-hidden mb-8 bg-white/60">
      <div class="p-4 sm:p-6 border-b border-purple-100 flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
       <h3 class="font-heading font-bold text-slate-800 text-lg">Quotation Items</h3><button id="add-item-btn" class="btn-primary px-4 py-2 bg-gradient-to-r from-purple-500 to-pink-500 text-white rounded-lg text-sm font-semibold hover:shadow-lg flex items-center justify-center gap-2 w-full sm:w-auto">
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
        </svg> Add Item </button>
      </div><!-- Desktop View -->
      <div class="hidden lg:block overflow-x-auto max-h-96">
       <table class="w-full">
        <thead class="bg-gradient-to-r from-purple-50 to-pink-50 sticky top-0 z-10">
         <tr>
          <th class="px-4 py-4 text-left text-xs font-semibold text-purple-700 uppercase tracking-wider">Item Description</th>
          <th class="px-2 py-4 text-center text-xs font-semibold text-purple-700 uppercase tracking-wider w-20">Qty</th>
          <th class="px-2 py-4 text-right text-xs font-semibold text-purple-700 uppercase tracking-wider w-28">Unit Price</th>
          <th class="px-2 py-4 text-right text-xs font-semibold text-purple-700 uppercase tracking-wider w-28">Discount</th>
          <th class="px-2 py-4 text-right text-xs font-semibold text-purple-700 uppercase tracking-wider w-28">Subtotal</th>
          <th class="px-2 py-4 text-center text-xs font-semibold text-purple-700 uppercase tracking-wider w-16">Actions</th>
         </tr>
        </thead>
        <tbody id="items-table-desktop" class="divide-y divide-purple-100"><!-- Items will be rendered here -->
        </tbody>
       </table>
      </div><!-- Mobile/Tablet View -->
      <div id="items-table-mobile" class="lg:hidden space-y-4 p-4 max-h-96 overflow-auto"><!-- Items will be rendered here -->
      </div>
      <div id="empty-state" class="hidden p-16 text-center">
       <svg class="w-20 h-20 mx-auto text-purple-200 mb-4" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
       </svg>
       <p class="text-slate-500 font-medium">No items added yet</p>
       <p class="text-slate-400 text-sm mt-1">Click "Add Item" to start building your quotation</p>
      </div><!-- Totals -->
      <div class="border-t border-purple-100 bg-gradient-to-r from-purple-50/50 to-pink-50/50 p-6">
       <div class="flex justify-end">
        <div class="w-full sm:w-80">
         <div class="flex justify-between py-3 text-slate-600 font-medium"><span>Total Items:</span> <span id="total-items" class="text-purple-600 font-semibold">0</span>
         </div>
         <div class="flex justify-between py-3 text-slate-600 font-medium"><span>Total Discount:</span> <span id="total-discount" class="text-emerald-600 font-semibold">Rs. 0.00</span>
         </div>
         <div class="flex justify-between py-4 border-t-2 border-purple-200 mt-2"><span class="text-lg font-bold text-slate-800">Grand Total:</span> <span id="grand-total" class="text-xl font-bold bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">Rs. 0.00</span>
         </div>
        </div>
       </div>
      </div>
     </div><!-- Action Buttons -->
     <div class="flex flex-col sm:flex-row gap-4 justify-center flex-wrap"><button id="preview-btn" class="btn-primary px-8 py-3.5 bg-gradient-to-r from-blue-500 to-cyan-500 text-white rounded-xl font-semibold flex items-center justify-center gap-3 hover:shadow-xl">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" /> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
       </svg> Preview </button> <button id="download-pdf-btn" class="btn-primary px-8 py-3.5 bg-gradient-to-r from-purple-500 to-pink-500 text-white rounded-xl font-semibold flex items-center justify-center gap-3 hover:shadow-xl">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
       </svg> Download PDF </button> <button id="send-email-btn" class="btn-primary px-8 py-3.5 bg-gradient-to-r from-emerald-500 to-teal-500 text-white rounded-xl font-semibold flex items-center justify-center gap-3 hover:shadow-xl">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
       </svg> Send Email </button> <button id="save-quotation-btn" class="btn-primary px-8 py-3.5 bg-gradient-to-r from-slate-600 to-slate-700 text-white rounded-xl font-semibold flex items-center justify-center gap-3 hover:shadow-xl">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7H5a2 2 0 00-2 2v9a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-3m-1 4l-3 3m0 0l-3-3m3 3V4" />
       </svg> Save </button> <button id="history-btn" class="btn-primary px-8 py-3.5 bg-gradient-to-r from-orange-500 to-amber-500 text-white rounded-xl font-semibold flex items-center justify-center gap-3 hover:shadow-xl">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
       </svg> History </button>
     </div>
    </main>
   </div><!-- Email Modal -->
   <div id="email-modal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-4 bg-slate-900/40 backdrop-blur-sm">
    <div class="relative bg-white rounded-2xl shadow-2xl w-full max-w-md p-6 card-modern">
     <h3 class="font-heading text-xl font-bold text-slate-800 mb-4">Send via Email</h3>
     <form id="email-form" class="space-y-4" onsubmit="handleEmailSubmit(event)">
      <div><label class="block text-sm font-semibold text-purple-600 mb-2">Customer Email</label> <input type="email" id="recipient-email" required readonly class="input-field w-full px-4 py-3 border border-purple-200 rounded-xl bg-purple-50" placeholder="customer@example.com">
      </div>
      <div><label class="block text-sm font-semibold text-purple-600 mb-2">Subject</label> <input type="text" id="email-subject" class="input-field w-full px-4 py-3 border border-purple-200 rounded-xl" value="Quotation from AL AMEEN TRADERS">
      </div>
      <div><label class="block text-sm font-semibold text-purple-600 mb-2">Message</label> <textarea id="email-message" rows="3" class="input-field w-full px-4 py-3 border border-purple-200 rounded-xl resize-none" placeholder="Please find attached our quotation for your review."></textarea>
      </div>
      <div class="flex gap-3 pt-2"><button type="button" id="cancel-email-btn" class="flex-1 px-4 py-3 border border-purple-200 text-slate-700 rounded-xl font-medium hover:bg-purple-50 transition-all">Cancel</button> <button type="submit" id="confirm-send-btn" class="flex-1 px-4 py-3 bg-gradient-to-r from-emerald-500 to-teal-500 text-white rounded-xl font-medium hover:shadow-lg transition-all">Send</button>
      </div>
     </form>
    </div>
   </div><!-- History Modal -->
   <div id="history-modal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-4 bg-slate-900/40 backdrop-blur-sm">
    <div class="relative bg-white rounded-2xl shadow-2xl w-full h-[90vh] max-w-4xl flex flex-col card-modern">
     <div class="flex items-center justify-between p-6 border-b border-purple-100">
      <h3 class="font-heading text-xl font-bold text-slate-800">Quotation History</h3><button id="close-history-btn" class="text-slate-500 hover:text-slate-700 transition-all p-1 hover:bg-slate-100 rounded-lg">
       <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
       </svg></button>
     </div>
     <div class="p-6 border-b border-purple-100 flex gap-3"><input type="text" id="history-search" placeholder="Search by quotation number or customer..." class="flex-1 px-4 py-2 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm"> <select id="history-sort" class="px-4 py-2 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm"> <option value="newest">Newest First</option> <option value="oldest">Oldest First</option> <option value="highest">Highest Amount</option> <option value="lowest">Lowest Amount</option> </select>
     </div>
     <div id="history-list" class="flex-1 overflow-auto p-6 bg-gradient-to-br from-slate-50 to-purple-50">
      <div class="text-center py-12">
       <svg class="w-16 h-16 mx-auto text-purple-200 mb-4" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
       </svg>
       <p class="text-slate-500 font-medium">No quotations saved yet</p>
       <p class="text-slate-400 text-sm mt-1">Click "Save" button to store quotations</p>
      </div>
     </div>
    </div>
   </div><!-- Preview Modal -->
   <div id="preview-modal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-2 sm:p-4 bg-slate-900/40 backdrop-blur-sm">
    <div class="relative bg-white rounded-2xl shadow-2xl w-full h-[95vh] sm:h-[90vh] max-w-4xl flex flex-col card-modern">
     <div class="flex items-center justify-between p-3 sm:p-6 border-b border-purple-100 flex-shrink-0">
      <h3 class="font-heading text-lg sm:text-xl font-bold text-slate-800">Quotation Preview</h3><button id="close-preview-btn" class="text-slate-500 hover:text-slate-700 transition-all p-1.5 hover:bg-slate-100 rounded-lg flex-shrink-0">
       <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
       </svg></button>
     </div>
     <div id="preview-content" class="flex-1 overflow-auto p-2 sm:p-6 bg-gradient-to-br from-slate-50 to-purple-50">
      <div id="preview-document" class="bg-white shadow-lg p-4 sm:p-8 md:p-12 mx-auto max-w-2xl rounded-xl text-sm sm:text-base"></div>
     </div>
    </div>
   </div><!-- Toast Container -->
   <div id="toast-container" class="fixed top-6 right-6 z-50 space-y-3"></div>
  </div>
  <script>
    const DEMO_CREDENTIALS = {
      username: 'alameen',
      password: 'alameen1995'
    };

    // Application State
    const state = {
      isLoggedIn: false,
      userEmail: '',
      staffName: '',
      items: [],
      savedQuotations: [],
      logoData: null,
      config: {
        shop_name: 'AL AMEEN TRADERS',
        contact_number: '011 2731769',
        address: '201/1, Galle Road, Dehiwala, Sri Lanka'
      }
    };

    const defaultConfig = {
      shop_name: 'AL AMEEN TRADERS',
      contact_number: '011 2731769',
      address: '201/1, Galle Road, Dehiwala, Sri Lanka'
    };

    // Initialize Element SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (config) => {
          state.config = { ...defaultConfig, ...config };
          updateBusinessDisplay();
        },
        mapToCapabilities: (config) => ({
          recolorables: [],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (config) => new Map([
          ['shop_name', config.shop_name || defaultConfig.shop_name],
          ['contact_number', config.contact_number || defaultConfig.contact_number],
          ['address', config.address || defaultConfig.address]
        ])
      });
    }

    // Data Handler
    const dataHandler = {
      onDataChanged(data) {
        const quotationItems = data.filter(item => item.type === 'quotation_item');
        const savedQuotations = data.filter(item => item.type === 'saved_quotation');
        state.items = quotationItems;
        state.savedQuotations = savedQuotations;
        renderItemsTable();
        updateTotals();
      }
    };

    async function initDataSdk() {
      if (window.dataSdk) {
        const result = await window.dataSdk.init(dataHandler);
        if (!result.isOk) {
          showToast('Failed to initialize data storage', 'error');
        }
      }
    }

    function showToast(message, type = 'success') {
      const container = document.getElementById('toast-container');
      const toast = document.createElement('div');
      const bgColor = type === 'success' ? 'bg-gradient-to-r from-emerald-500 to-teal-500' : type === 'error' ? 'bg-gradient-to-r from-red-500 to-pink-500' : 'bg-gradient-to-r from-blue-500 to-cyan-500';
      toast.className = `toast ${bgColor} text-white px-6 py-3.5 rounded-xl shadow-lg flex items-center gap-3 backdrop-blur`;
      toast.innerHTML = `
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          ${type === 'success' 
            ? '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>'
            : type === 'error'
            ? '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>'
            : '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>'}
        </svg>
        <span>${message}</span>
      `;
      container.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    function handleLogin(e) {
      e.preventDefault();
      const username = document.getElementById('login-username').value.trim();
      const password = document.getElementById('login-password').value.trim();
      const staffName = document.getElementById('login-staff-name').value.trim();
      const errorDiv = document.getElementById('login-error');

      if (!username || !password || !staffName) {
        errorDiv.textContent = 'Please fill in all fields.';
        errorDiv.classList.remove('hidden');
        return;
      }

      if (username === DEMO_CREDENTIALS.username && password === DEMO_CREDENTIALS.password) {
        state.isLoggedIn = true;
        state.userEmail = username;
        state.staffName = staffName;
        
        document.getElementById('login-screen').classList.add('hidden');
        document.getElementById('dashboard').classList.remove('hidden');
        document.getElementById('user-email').textContent = username;
        document.getElementById('staff-name-display').textContent = '👤 ' + staffName;
        document.getElementById('staff-name').value = staffName;
        document.getElementById('quotation-date').value = new Date().toISOString().split('T')[0];
        document.getElementById('quotation-number').value = 'QT-' + Date.now().toString().slice(-6);
        errorDiv.classList.add('hidden');
        showToast('Welcome ' + staffName + '!', 'success');
      } else {
        errorDiv.textContent = 'Invalid credentials. Try: alameen / alameen1995';
        errorDiv.classList.remove('hidden');
      }
    }

    function handleLogout() {
      state.isLoggedIn = false;
      state.staffName = '';
      state.items = [];
      state.logoData = null;
      document.getElementById('dashboard').classList.add('hidden');
      document.getElementById('login-screen').classList.remove('hidden');
      document.getElementById('login-username').value = '';
      document.getElementById('login-password').value = '';
      document.getElementById('login-staff-name').value = '';
      document.getElementById('login-error').classList.add('hidden');
    }

    function updateBusinessDisplay() {
      document.getElementById('display-shop-name').textContent = state.config.shop_name;
      document.getElementById('display-contact').textContent = '📞 ' + state.config.contact_number;
      document.getElementById('display-address').textContent = '📍 ' + state.config.address;
      document.getElementById('header-shop-name').textContent = state.config.shop_name;
    }

    function handleLogoUpload(e) {
      const file = e.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = function(event) {
          state.logoData = event.target.result;
          const logoImage = document.getElementById('logo-image');
          const logoPlaceholder = document.getElementById('logo-placeholder');
          logoImage.src = state.logoData;
          logoImage.classList.remove('hidden');
          logoPlaceholder.classList.add('hidden');
          showToast('Logo uploaded successfully', 'success');
        };
        reader.readAsDataURL(file);
      }
    }

    async function addItem() {
      if (state.items.length >= 999) {
        showToast('Maximum limit of 999 items reached', 'error');
        return;
      }

      const newItem = {
        type: 'quotation_item',
        item_description: '',
        quantity: 1,
        selling_price: 0,
        discount_amount: 0,
        created_at: new Date().toISOString()
      };

      if (window.dataSdk) {
        const result = await window.dataSdk.create(newItem);
        if (!result.isOk) {
          showToast('Failed to add item', 'error');
        }
      }
    }

    async function updateItem(item, field, value) {
      item[field] = value;
      if (window.dataSdk) {
        const result = await window.dataSdk.update(item);
        if (!result.isOk) {
          showToast('Failed to update item', 'error');
        }
      }
    }

    async function deleteItem(item) {
      if (window.dataSdk) {
        const result = await window.dataSdk.delete(item);
        if (result.isOk) {
          showToast('Item removed', 'success');
        } else {
          showToast('Failed to remove item', 'error');
        }
      }
    }

    function renderItemsTable() {
      const tbodyDesktop = document.getElementById('items-table-desktop');
      const mobileContainer = document.getElementById('items-table-mobile');
      const emptyState = document.getElementById('empty-state');

      if (state.items.length === 0) {
        tbodyDesktop.innerHTML = '';
        mobileContainer.innerHTML = '';
        emptyState.classList.remove('hidden');
        return;
      }

      emptyState.classList.add('hidden');
      
      // Desktop rendering
      const existingRows = new Map();
      tbodyDesktop.querySelectorAll('tr[data-id]').forEach(row => {
        existingRows.set(row.dataset.id, row);
      });

      state.items.forEach((item, index) => {
        const itemId = item.__backendId;
        const subtotal = calculateSubtotal(item);
        
        if (existingRows.has(itemId)) {
          const row = existingRows.get(itemId);
          const subtotalCell = row.querySelector('.subtotal');
          if (subtotalCell) {
            subtotalCell.textContent = formatCurrency(subtotal);
          }
          existingRows.delete(itemId);
        } else {
          const row = document.createElement('tr');
          row.className = 'table-row transition-colors';
          row.dataset.id = itemId;
          row.innerHTML = `
            <td class="px-4 py-3">
              <input type="text" value="${escapeHtml(item.item_description || '')}" 
                class="w-full px-2 py-2 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm"
                placeholder="Enter item description"
                data-field="item_description">
            </td>
            <td class="px-2 py-3">
              <input type="number" value="${item.quantity || 1}" min="1"
                class="w-full px-2 py-2 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm text-center"
                data-field="quantity">
            </td>
            <td class="px-2 py-3">
              <input type="number" value="${item.selling_price || 0}" min="0" step="0.01"
                class="w-full px-2 py-2 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm text-right"
                data-field="selling_price">
            </td>
            <td class="px-2 py-3">
              <input type="number" value="${item.discount_amount || 0}" min="0" step="0.01"
                class="w-full px-2 py-2 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm text-right"
                data-field="discount_amount">
            </td>
            <td class="px-2 py-3 text-right font-semibold text-slate-800 text-sm subtotal">
              ${formatCurrency(subtotal)}
            </td>
            <td class="px-2 py-3 text-center">
              <button class="delete-btn p-1.5 text-red-500 hover:bg-red-50 rounded-lg transition-colors" title="Remove item">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/>
                </svg>
              </button>
            </td>
          `;

          row.querySelectorAll('input').forEach(input => {
            input.addEventListener('change', () => {
              const field = input.dataset.field;
              let value = input.value;
              if (field !== 'item_description') {
                value = parseFloat(value) || 0;
              }
              updateItem(item, field, value);
            });
          });

          row.querySelector('.delete-btn').addEventListener('click', () => {
            row.innerHTML = `
              <td colspan="6" class="px-4 py-3 text-center">
                <span class="text-slate-600 text-sm mr-3">Delete this item?</span>
                <button class="confirm-delete px-3 py-1.5 bg-gradient-to-r from-red-500 to-pink-500 text-white rounded-lg text-xs font-medium mr-2 inline-block">Yes</button>
                <button class="cancel-delete px-3 py-1.5 bg-slate-200 text-slate-700 rounded-lg text-xs font-medium inline-block">Cancel</button>
              </td>
            `;
            row.querySelector('.confirm-delete').addEventListener('click', () => deleteItem(item));
            row.querySelector('.cancel-delete').addEventListener('click', () => renderItemsTable());
          });

          tbodyDesktop.appendChild(row);
        }
      });

      existingRows.forEach(row => row.remove());

      // Mobile rendering
      mobileContainer.innerHTML = state.items.map((item, index) => {
        const itemId = item.__backendId;
        const subtotal = calculateSubtotal(item);
        return `
          <div class="bg-white border border-purple-200 rounded-lg p-4 shadow-sm" data-mobile-id="${itemId}">
            <div class="flex items-center justify-between mb-4">
              <span class="text-xs font-bold text-purple-600 uppercase bg-purple-100 px-2.5 py-1 rounded">Item ${index + 1}</span>
              <button class="mobile-delete-btn p-2 text-red-500 hover:bg-red-50 rounded-lg transition-colors" title="Remove item">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/>
                </svg>
              </button>
            </div>
            
            <div class="space-y-3">
              <div>
                <label class="block text-xs font-semibold text-purple-600 mb-1.5">Item Description</label>
                <input type="text" value="${escapeHtml(item.item_description || '')}" 
                  class="w-full px-3 py-2.5 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm focus:ring-2 focus:ring-purple-100"
                  placeholder="Enter item description"
                  data-field="item_description" data-item-id="${itemId}">
              </div>
              
              <div class="grid grid-cols-2 gap-3">
                <div>
                  <label class="block text-xs font-semibold text-purple-600 mb-1.5">Quantity</label>
                  <input type="number" value="${item.quantity || 1}" min="1"
                    class="w-full px-3 py-2.5 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm focus:ring-2 focus:ring-purple-100 text-center"
                    data-field="quantity" data-item-id="${itemId}">
                </div>
                <div>
                  <label class="block text-xs font-semibold text-purple-600 mb-1.5">Unit Price</label>
                  <input type="number" value="${item.selling_price || 0}" min="0" step="0.01"
                    class="w-full px-3 py-2.5 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm focus:ring-2 focus:ring-purple-100 text-right"
                    data-field="selling_price" data-item-id="${itemId}">
                </div>
              </div>

              <div class="grid grid-cols-2 gap-3">
                <div>
                  <label class="block text-xs font-semibold text-purple-600 mb-1.5">Discount Per Item</label>
                  <input type="number" value="${item.discount_amount || 0}" min="0" step="0.01"
                    class="w-full px-3 py-2.5 border border-purple-200 rounded-lg focus:outline-none focus:border-purple-500 text-sm focus:ring-2 focus:ring-purple-100 text-right"
                    data-field="discount_amount" data-item-id="${itemId}">
                </div>
                <div>
                  <label class="block text-xs font-semibold text-purple-600 mb-1.5">Subtotal</label>
                  <div class="px-3 py-2.5 bg-gradient-to-r from-purple-50 to-pink-50 border border-purple-200 rounded-lg text-right font-bold text-purple-600 text-sm mobile-subtotal">
                    ${formatCurrency(subtotal)}
                  </div>
                </div>
              </div>
            </div>
          </div>
        `;
      }).join('');

      // Add event listeners for mobile inputs
      mobileContainer.querySelectorAll('input').forEach(input => {
        input.addEventListener('change', () => {
          const itemId = input.dataset.itemId;
          const field = input.dataset.field;
          const item = state.items.find(i => i.__backendId === itemId);
          if (item) {
            let value = input.value;
            if (field !== 'item_description') {
              value = parseFloat(value) || 0;
            }
            updateItem(item, field, value);
          }
        });
      });

      // Add event listeners for mobile delete buttons
      mobileContainer.querySelectorAll('.mobile-delete-btn').forEach(btn => {
        btn.addEventListener('click', function() {
          const mobileCard = this.closest('[data-mobile-id]');
          const itemId = mobileCard.dataset.mobileId;
          const item = state.items.find(i => i.__backendId === itemId);
          if (item) {
            const originalHTML = mobileCard.innerHTML;
            mobileCard.innerHTML = `
              <div class="text-center space-y-3">
                <p class="text-slate-600 font-medium">Delete this item?</p>
                <div class="flex gap-2 justify-center">
                  <button class="confirm-delete-mobile flex-1 px-3 py-2.5 bg-gradient-to-r from-red-500 to-pink-500 text-white rounded-lg text-sm font-medium">Yes, Delete</button>
                  <button class="cancel-delete-mobile flex-1 px-3 py-2.5 bg-slate-200 text-slate-700 rounded-lg text-sm font-medium">Cancel</button>
                </div>
              </div>
            `;
            mobileCard.querySelector('.confirm-delete-mobile').addEventListener('click', () => deleteItem(item));
            mobileCard.querySelector('.cancel-delete-mobile').addEventListener('click', () => renderItemsTable());
          }
        });
      });
    }

    function calculateSubtotal(item) {
      const qty = parseFloat(item.quantity) || 0;
      const price = parseFloat(item.selling_price) || 0;
      const discountPerItem = parseFloat(item.discount_amount) || 0;
      return Math.max(0, (qty * price) - (qty * discountPerItem));
    }

    function updateTotals() {
      let totalDiscount = 0;
      let grandTotal = 0;

      state.items.forEach(item => {
        const qty = parseFloat(item.quantity) || 0;
        const discountPerItem = parseFloat(item.discount_amount) || 0;
        totalDiscount += (qty * discountPerItem);
        grandTotal += calculateSubtotal(item);
      });

      document.getElementById('total-items').textContent = state.items.length;
      document.getElementById('total-discount').textContent = formatCurrency(totalDiscount);
      document.getElementById('grand-total').textContent = formatCurrency(grandTotal);
    }

    function formatCurrency(amount) {
      return 'Rs. ' + parseFloat(amount).toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    }

    function escapeHtml(text) {
      const div = document.createElement('div');
      div.textContent = text;
      return div.innerHTML;
    }

    function generatePreviewHTML() {
      let totalDiscount = 0;
      let grandTotal = 0;

      state.items.forEach(item => {
        const qty = parseFloat(item.quantity) || 0;
        const discountPerItem = parseFloat(item.discount_amount) || 0;
        totalDiscount += (qty * discountPerItem);
        grandTotal += calculateSubtotal(item);
      });

      const quotationNo = document.getElementById('quotation-number').value || 'QT-001';
      const quotationDate = document.getElementById('quotation-date').value || new Date().toISOString().split('T')[0];
      const customerName = document.getElementById('customer-name').value || 'Customer Name';
      const customerEmail = document.getElementById('customer-email').value || 'customer@example.com';

      let html = `
        <style>
          @media (max-width: 640px) {
            .preview-title { font-size: 24px !important; }
            .preview-shop-name { font-size: 14px !important; }
            .preview-contact { font-size: 11px !important; }
            .preview-header-info { font-size: 12px !important; display: block !important; }
            .preview-header-right { width: 100% !important; text-align: left !important; margin-top: 12px !important; }
            .preview-table { font-size: 11px !important; }
            .preview-table th, .preview-table td { padding: 8px 4px !important; }
            .preview-customer { font-size: 12px !important; }
            .preview-totals { font-size: 11px !important; }
            .preview-totals-right { width: 100% !important; text-align: right !important; margin-top: 20px !important; }
            .preview-footer { font-size: 10px !important; }
          }
          
          @media (min-width: 641px) and (max-width: 1024px) {
            .preview-title { font-size: 28px !important; }
            .preview-shop-name { font-size: 16px !important; }
            .preview-contact { font-size: 12px !important; }
            .preview-header-info { font-size: 13px !important; }
            .preview-table { font-size: 12px !important; }
            .preview-table th, .preview-table td { padding: 10px 6px !important; }
            .preview-customer { font-size: 13px !important; }
            .preview-totals { font-size: 12px !important; }
            .preview-footer { font-size: 11px !important; }
          }
          
          @media (min-width: 1025px) {
            .preview-title { font-size: 36px !important; }
            .preview-shop-name { font-size: 18px !important; }
            .preview-contact { font-size: 14px !important; }
            .preview-header-info { font-size: 14px !important; display: flex !important; justify-content: space-between !important; }
            .preview-header-right { width: 50% !important; text-align: right !important; }
            .preview-table { font-size: 13px !important; }
            .preview-table th, .preview-table td { padding: 12px 8px !important; }
            .preview-customer { font-size: 14px !important; }
            .preview-totals { font-size: 13px !important; }
            .preview-header-info div { flex: 1; }
            .preview-totals-right { width: 300px !important; }
            .preview-footer { font-size: 12px !important; }
          }
          
          .preview-table { width: 100%; border-collapse: collapse; margin: 20px 0; }
          .preview-table thead tr { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; }
          .preview-table th { text-align: left; font-weight: 600; }
          .preview-table td { border: 1px solid #e5e7eb; }
          .preview-table tbody tr:nth-child(even) { background-color: #f8fafc; }
          .preview-table tbody tr:nth-child(odd) { background-color: #ffffff; }
          
          .preview-logo { max-width: 60px; height: auto; margin: 0 auto 16px; display: block; }
          .preview-center { text-align: center; margin-bottom: 24px; }
          .preview-header-info { gap: 24px; margin: 24px 0; }
          .preview-header-section { text-align: left; }
          .preview-header-right { padding-left: 0; }
          .preview-customer { margin: 20px 0; padding: 12px; background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%); border: 1px solid rgba(102, 126, 234, 0.2); border-radius: 8px; }
          .preview-totals { display: flex; justify-content: flex-end; margin-top: 24px; }
          .preview-totals-section { }
          .preview-totals-row { display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid #e5e7eb; }
          .preview-totals-grand { border: 2px solid #667eea !important; padding: 12px 0 !important; font-size: 16px !important; font-weight: 800; margin-top: 8px; }
          .preview-totals-grand span:last-child { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
          .preview-footer { text-align: center; margin-top: 32px; padding-top: 16px; border-top: 1px solid #e5e7eb; color: #888888; }
          .preview-contact-text { color: #666666; margin: 4px 0; }
        </style>
        
        <div class="preview-center">
      `;
      
      if (state.logoData) {
        html += `<img src="${state.logoData}" alt="Logo" class="preview-logo">`;
      }
      
      html += `
          <h1 class="preview-title" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; font-weight: bold; letter-spacing: 2px; margin: 16px 0;">QUOTATION</h1>
        </div>
        
        <div class="preview-center">
          <h2 class="preview-shop-name" style="font-weight: bold; margin: 8px 0;">${state.config.shop_name}</h2>
          <p class="preview-contact preview-contact-text">📞 ${state.config.contact_number}</p>
          <p class="preview-contact preview-contact-text">📍 ${state.config.address}</p>
        </div>
        
        <div class="preview-header-info">
          <div class="preview-header-section">
            <p class="preview-header-info"><strong>Quotation No:</strong> <span style="font-family: monospace;">${quotationNo}</span></p>
            <p class="preview-header-info"><strong>Date:</strong> ${quotationDate}</p>
          </div>
          <div class="preview-header-section preview-header-right">
            <p class="preview-header-info"><strong>Created by:</strong> ${state.staffName}</p>
          </div>
        </div>
        
        <div class="preview-customer">
          <p class="preview-customer"><strong>Customer:</strong> ${customerName}</p>
          <p class="preview-customer"><strong>Email:</strong> ${customerEmail}</p>
        </div>
        
        <table class="preview-table">
          <thead>
            <tr>
              <th style="text-align: left;">Item Description</th>
              <th style="text-align: center; width: 60px;">Qty</th>
              <th style="text-align: right; width: 80px;">Unit Price</th>
              <th style="text-align: right; width: 80px;">Discount</th>
              <th style="text-align: right; width: 80px;">Subtotal</th>
            </tr>
          </thead>
          <tbody>
      `;

      state.items.forEach((item) => {
        const subtotal = calculateSubtotal(item);
        html += `
          <tr>
            <td style="text-align: left; word-break: break-word;">${escapeHtml(item.item_description || '')}</td>
            <td style="text-align: center;">${item.quantity || 0}</td>
            <td style="text-align: right;">${formatCurrency(item.selling_price || 0)}</td>
            <td style="text-align: right;">${formatCurrency(item.discount_amount || 0)}</td>
            <td style="text-align: right; font-weight: bold;">${formatCurrency(subtotal)}</td>
          </tr>
        `;
      });

      html += `
          </tbody>
        </table>
        
        <div class="preview-totals">
          <div class="preview-totals-section">
            <div class="preview-totals-row">
              <span>Total Items:</span>
              <span style="font-weight: bold;">${state.items.length}</span>
            </div>
            <div class="preview-totals-row">
              <span>Total Discount:</span>
              <span style="font-weight: bold; color: #10b981;">${formatCurrency(totalDiscount)}</span>
            </div>
            <div class="preview-totals-row preview-totals-grand">
              <span>Grand Total:</span>
              <span>${formatCurrency(grandTotal)}</span>
            </div>
          </div>
        </div>
        
        <div class="preview-footer">
          <p>Thank you for your business!</p>
        </div>
      `;

      return html;
    }

    function openPreview() {
      const previewDocument = document.getElementById('preview-document');
      previewDocument.innerHTML = generatePreviewHTML();
      document.getElementById('preview-modal').classList.remove('hidden');
    }

    function closePreview() {
      document.getElementById('preview-modal').classList.add('hidden');
    }

    function renderHistoryList() {
      const searchTerm = document.getElementById('history-search').value.toLowerCase();
      const sortBy = document.getElementById('history-sort').value;
      const historyList = document.getElementById('history-list');

      let filtered = state.savedQuotations.filter(q => 
        q.quotation_number.toLowerCase().includes(searchTerm) || 
        q.customer_name.toLowerCase().includes(searchTerm)
      );

      filtered.sort((a, b) => {
        switch(sortBy) {
          case 'oldest': return new Date(a.created_at) - new Date(b.created_at);
          case 'highest': return b.grand_total - a.grand_total;
          case 'lowest': return a.grand_total - b.grand_total;
          case 'newest': 
          default: return new Date(b.created_at) - new Date(a.created_at);
        }
      });

      if (filtered.length === 0) {
        historyList.innerHTML = `
          <div class="text-center py-12">
            <svg class="w-16 h-16 mx-auto text-purple-200 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/>
            </svg>
            <p class="text-slate-500 font-medium">No quotations found</p>
            <p class="text-slate-400 text-sm mt-1">Try adjusting your search or sort options</p>
          </div>
        `;
        return;
      }

      historyList.innerHTML = filtered.map((q, index) => {
        const date = new Date(q.quotation_date);
        const formattedDate = date.toLocaleDateString('en-US', { year: 'numeric', month: 'short', day: 'numeric' });
        const bgColor = index % 2 === 0 ? 'bg-white' : 'bg-purple-50';
        
        return `
          <div class="${bgColor} p-4 rounded-lg border border-purple-100 mb-3 hover:shadow-md transition-shadow">
            <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
              <div class="flex-grow">
                <div class="flex items-center gap-3 mb-2">
                  <h4 class="font-bold text-purple-700 text-lg">${escapeHtml(q.quotation_number)}</h4>
                  <span class="text-xs px-3 py-1 bg-purple-100 text-purple-700 rounded-full font-semibold">${formattedDate}</span>
                </div>
                <div class="grid grid-cols-2 sm:grid-cols-4 gap-3 text-sm">
                  <div>
                    <p class="text-slate-500 text-xs">Customer</p>
                    <p class="font-medium text-slate-800">${escapeHtml(q.customer_name)}</p>
                  </div>
                  <div>
                    <p class="text-slate-500 text-xs">Email</p>
                    <p class="font-medium text-slate-800 truncate">${escapeHtml(q.customer_email || 'N/A')}</p>
                  </div>
                  <div>
                    <p class="text-slate-500 text-xs">Staff</p>
                    <p class="font-medium text-slate-800">${escapeHtml(q.staff_name)}</p>
                  </div>
                  <div>
                    <p class="text-slate-500 text-xs">Amount</p>
                    <p class="font-bold text-purple-600">${formatCurrency(q.grand_total)}</p>
                  </div>
                </div>
              </div>
              <div class="flex gap-2">
                <button class="load-history-btn px-4 py-2 bg-gradient-to-r from-blue-500 to-cyan-500 text-white rounded-lg text-sm font-medium hover:shadow-lg transition-all" data-id="${q.__backendId}">
                  Load
                </button>
                <button class="delete-history-btn px-4 py-2 bg-red-100 text-red-600 rounded-lg text-sm font-medium hover:bg-red-200 transition-all" data-id="${q.__backendId}">
                  Delete
                </button>
              </div>
            </div>
          </div>
        `;
      }).join('');

      document.querySelectorAll('.load-history-btn').forEach(btn => {
        btn.addEventListener('click', function() {
          loadQuotationFromHistory(this.dataset.id);
        });
      });

      document.querySelectorAll('.delete-history-btn').forEach(btn => {
        btn.addEventListener('click', function() {
          deleteQuotationFromHistory(this.dataset.id);
        });
      });
    }

    async function loadQuotationFromHistory(quotationId) {
      const quotation = state.savedQuotations.find(q => q.__backendId === quotationId);
      if (!quotation) return;

      document.getElementById('quotation-number').value = quotation.quotation_number;
      document.getElementById('quotation-date').value = quotation.quotation_date;
      document.getElementById('customer-name').value = quotation.customer_name;
      document.getElementById('customer-email').value = quotation.customer_email;

      if (quotation.logo_data) {
        state.logoData = quotation.logo_data;
        const logoImage = document.getElementById('logo-image');
        const logoPlaceholder = document.getElementById('logo-placeholder');
        logoImage.src = state.logoData;
        logoImage.classList.remove('hidden');
        logoPlaceholder.classList.add('hidden');
      }

      state.config = quotation.shop_config_json ? JSON.parse(quotation.shop_config_json) : state.config;
      updateBusinessDisplay();

      if (window.dataSdk && quotation.items_json) {
        const items = JSON.parse(quotation.items_json);
        for (const item of items) {
          const { __backendId, ...newItem } = item;
          newItem.type = 'quotation_item';
          const result = await window.dataSdk.create(newItem);
          if (!result.isOk) {
            showToast('Error loading some items', 'error');
          }
        }
      }

      document.getElementById('history-modal').classList.add('hidden');
      showToast('Quotation loaded successfully!', 'success');
    }

    async function deleteQuotationFromHistory(quotationId) {
      const quotation = state.savedQuotations.find(q => q.__backendId === quotationId);
      if (!quotation) return;

      if (window.dataSdk) {
        const result = await window.dataSdk.delete(quotation);
        if (result.isOk) {
          showToast('Quotation deleted', 'success');
          renderHistoryList();
        } else {
          showToast('Failed to delete quotation', 'error');
        }
      }
    }

    async function handleEmailSubmit(e) {
      e.preventDefault();
      const recipientEmail = document.getElementById('recipient-email').value;
      const subject = document.getElementById('email-subject').value;
      const message = document.getElementById('email-message').value;

      if (!recipientEmail) {
        showToast('Please enter recipient email', 'error');
        return;
      }

      try {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF();
        
        let yPos = 20;
        const quotationNo = document.getElementById('quotation-number').value || 'quotation';
        const quotationDate = document.getElementById('quotation-date').value || new Date().toISOString().split('T')[0];
        const customerName = document.getElementById('customer-name').value || 'Customer';

        if (state.logoData) {
          try {
            doc.addImage(state.logoData, 'JPEG', 15, yPos, 40, 30);
            yPos += 35;
          } catch (e) {
            console.error('Logo error', e);
          }
        }

        doc.setFontSize(24);
        doc.setTextColor(102, 126, 234);
        doc.text('QUOTATION', 105, yPos, { align: 'center' });
        yPos += 15;

        doc.setFontSize(14);
        doc.setTextColor(0, 0, 0);
        doc.text(state.config.shop_name, 105, yPos, { align: 'center' });
        yPos += 7;
        doc.setFontSize(10);
        doc.setTextColor(100, 100, 100);
        doc.text(state.config.contact_number, 105, yPos, { align: 'center' });
        yPos += 5;
        doc.text(state.config.address, 105, yPos, { align: 'center' });
        yPos += 15;

        doc.setTextColor(0, 0, 0);
        doc.setFontSize(10);
        doc.text(`Quotation No: ${quotationNo}`, 15, yPos);
        doc.text(`Date: ${quotationDate}`, 150, yPos);
        yPos += 7;
        doc.text(`Customer: ${customerName}`, 15, yPos);
        yPos += 7;
        doc.text(`Created by: ${state.staffName}`, 15, yPos);
        yPos += 15;

        const tableData = state.items.map(item => [
          item.item_description || '',
          (item.quantity || 0).toString(),
          formatCurrency(item.selling_price || 0),
          formatCurrency(item.discount_amount || 0),
          formatCurrency(calculateSubtotal(item))
        ]);

        if (tableData.length > 0) {
          doc.autoTable({
            startY: yPos,
            head: [['Item Description', 'Qty', 'Unit Price', 'Discount', 'Subtotal']],
            body: tableData,
            theme: 'striped',
            headStyles: { fillColor: [102, 126, 234], textColor: 255 },
            columnStyles: {
              0: { cellWidth: 70 },
              1: { cellWidth: 20, halign: 'center' },
              2: { cellWidth: 30, halign: 'right' },
              3: { cellWidth: 30, halign: 'right' },
              4: { cellWidth: 30, halign: 'right' }
            }
          });
          yPos = doc.lastAutoTable.finalY + 10;
        }

        let totalDiscount = 0;
        let grandTotal = 0;
        state.items.forEach(item => {
          const qty = parseFloat(item.quantity) || 0;
          const discountPerItem = parseFloat(item.discount_amount) || 0;
          totalDiscount += (qty * discountPerItem);
          grandTotal += calculateSubtotal(item);
        });

        doc.setFontSize(11);
        doc.text(`Total Items: ${state.items.length}`, 140, yPos, { align: 'right' });
        yPos += 7;
        doc.text(`Total Discount: ${formatCurrency(totalDiscount)}`, 140, yPos, { align: 'right' });
        yPos += 10;
        doc.setFontSize(14);
        doc.setTextColor(102, 126, 234);
        doc.text(`Grand Total: ${formatCurrency(grandTotal)}`, 140, yPos, { align: 'right' });

        yPos += 25;
        doc.setFontSize(9);
        doc.setTextColor(128, 128, 128);
        doc.text('Thank you for your business!', 105, yPos, { align: 'center' });

        doc.save(`${quotationNo}.pdf`);
        
        const mailtoLink = `mailto:${recipientEmail}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(message)}`;
        window.open(mailtoLink);
        
        document.getElementById('email-modal').classList.add('hidden');
        showToast('Email client opened! PDF saved - attach and send.', 'success');
      } catch (error) {
        console.error('Email error:', error);
        showToast('Error preparing email', 'error');
      }
    }

    // Event Listeners
    document.getElementById('logo-preview').addEventListener('click', () => document.getElementById('logo-upload').click());
    document.getElementById('logo-upload').addEventListener('change', handleLogoUpload);
    document.getElementById('add-item-btn').addEventListener('click', addItem);
    document.getElementById('preview-btn').addEventListener('click', openPreview);
    document.getElementById('close-preview-btn').addEventListener('click', closePreview);
    document.getElementById('logout-btn').addEventListener('click', handleLogout);
    document.getElementById('cancel-email-btn').addEventListener('click', () => document.getElementById('email-modal').classList.add('hidden'));

    document.getElementById('history-btn').addEventListener('click', () => {
      document.getElementById('history-modal').classList.remove('hidden');
      renderHistoryList();
    });

    document.getElementById('close-history-btn').addEventListener('click', () => {
      document.getElementById('history-modal').classList.add('hidden');
    });

    document.getElementById('history-search').addEventListener('input', renderHistoryList);
    document.getElementById('history-sort').addEventListener('change', renderHistoryList);

    document.getElementById('preview-modal').addEventListener('click', (e) => {
      if (e.target === e.currentTarget) closePreview();
    });

    document.getElementById('history-modal').addEventListener('click', (e) => {
      if (e.target === e.currentTarget) document.getElementById('history-modal').classList.add('hidden');
    });

    document.getElementById('email-modal').addEventListener('click', (e) => {
      if (e.target === e.currentTarget) document.getElementById('email-modal').classList.add('hidden');
    });

    document.getElementById('download-pdf-btn').addEventListener('click', async function() {
      try {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF();
        
        let yPos = 20;
        const quotationNo = document.getElementById('quotation-number').value || 'quotation';
        const quotationDate = document.getElementById('quotation-date').value || new Date().toISOString().split('T')[0];
        const customerName = document.getElementById('customer-name').value || 'Customer';
        const customerEmail = document.getElementById('customer-email').value || 'N/A';

        if (state.logoData) {
          try {
            doc.addImage(state.logoData, 'JPEG', 15, yPos, 40, 30);
            yPos += 35;
          } catch (e) {
            console.error('Logo error', e);
          }
        }

        doc.setFontSize(24);
        doc.setTextColor(102, 126, 234);
        doc.text('QUOTATION', 105, yPos, { align: 'center' });
        yPos += 15;

        doc.setFontSize(14);
        doc.setTextColor(0, 0, 0);
        doc.text(state.config.shop_name, 105, yPos, { align: 'center' });
        yPos += 7;
        doc.setFontSize(10);
        doc.setTextColor(100, 100, 100);
        doc.text(state.config.contact_number, 105, yPos, { align: 'center' });
        yPos += 5;
        doc.text(state.config.address, 105, yPos, { align: 'center' });
        yPos += 15;

        doc.setTextColor(0, 0, 0);
        doc.setFontSize(10);
        doc.text(`Quotation No: ${quotationNo}`, 15, yPos);
        doc.text(`Date: ${quotationDate}`, 150, yPos);
        yPos += 7;
        doc.text(`Customer: ${customerName}`, 15, yPos);
        doc.text(`Email: ${customerEmail}`, 150, yPos);
        yPos += 7;
        doc.text(`Created by: ${state.staffName}`, 15, yPos);
        yPos += 15;

        const tableData = state.items.map(item => [
          item.item_description || '',
          (item.quantity || 0).toString(),
          formatCurrency(item.selling_price || 0),
          formatCurrency(item.discount_amount || 0),
          formatCurrency(calculateSubtotal(item))
        ]);

        if (tableData.length > 0) {
          doc.autoTable({
            startY: yPos,
            head: [['Item Description', 'Qty', 'Unit Price', 'Discount', 'Subtotal']],
            body: tableData,
            theme: 'striped',
            headStyles: { fillColor: [102, 126, 234], textColor: 255 },
            columnStyles: {
              0: { cellWidth: 70 },
              1: { cellWidth: 20, halign: 'center' },
              2: { cellWidth: 30, halign: 'right' },
              3: { cellWidth: 30, halign: 'right' },
              4: { cellWidth: 30, halign: 'right' }
            }
          });
          yPos = doc.lastAutoTable.finalY + 10;
        }

        let totalDiscount = 0;
        let grandTotal = 0;
        state.items.forEach(item => {
          const qty = parseFloat(item.quantity) || 0;
          const discountPerItem = parseFloat(item.discount_amount) || 0;
          totalDiscount += (qty * discountPerItem);
          grandTotal += calculateSubtotal(item);
        });

        doc.setFontSize(11);
        doc.text(`Total Items: ${state.items.length}`, 140, yPos, { align: 'right' });
        yPos += 7;
        doc.text(`Total Discount: ${formatCurrency(totalDiscount)}`, 140, yPos, { align: 'right' });
        yPos += 10;
        doc.setFontSize(14);
        doc.setTextColor(102, 126, 234);
        doc.text(`Grand Total: ${formatCurrency(grandTotal)}`, 140, yPos, { align: 'right' });

        yPos += 25;
        doc.setFontSize(9);
        doc.setTextColor(128, 128, 128);
        doc.text('Thank you for your business!', 105, yPos, { align: 'center' });

        doc.save(`${quotationNo}.pdf`);
        showToast('PDF downloaded successfully!', 'success');
      } catch (error) {
        console.error('PDF error:', error);
        showToast('Failed to generate PDF', 'error');
      }
    });

    document.getElementById('send-email-btn').addEventListener('click', () => {
      const customerEmail = document.getElementById('customer-email').value;
      if (!customerEmail) {
        showToast('Please enter customer email address first', 'error');
        return;
      }
      document.getElementById('recipient-email').value = customerEmail;
      document.getElementById('email-modal').classList.remove('hidden');
    });

    document.getElementById('save-quotation-btn').addEventListener('click', async function() {
      const quotationNumber = document.getElementById('quotation-number').value;
      const quotationDate = document.getElementById('quotation-date').value;
      const customerName = document.getElementById('customer-name').value;
      const customerEmail = document.getElementById('customer-email').value;

      if (!quotationNumber || !customerName || state.items.length === 0) {
        showToast('Please fill all required fields and add items', 'error');
        return;
      }

      if (state.savedQuotations.length >= 100) {
        showToast('Maximum 100 saved quotations reached. Please delete old ones.', 'error');
        return;
      }

      let totalDiscount = 0;
      let grandTotal = 0;
      state.items.forEach(item => {
        const qty = parseFloat(item.quantity) || 0;
        const discountPerItem = parseFloat(item.discount_amount) || 0;
        totalDiscount += (qty * discountPerItem);
        grandTotal += calculateSubtotal(item);
      });

      const quotationData = {
        type: 'saved_quotation',
        quotation_number: quotationNumber,
        quotation_date: quotationDate,
        customer_name: customerName,
        customer_email: customerEmail,
        staff_name: state.staffName,
        items_json: JSON.stringify(state.items),
        total_discount: totalDiscount,
        grand_total: grandTotal,
        logo_data: state.logoData || '',
        shop_config_json: JSON.stringify(state.config),
        created_at: new Date().toISOString()
      };

      if (window.dataSdk) {
        const result = await window.dataSdk.create(quotationData);
        if (result.isOk) {
          showToast('Quotation saved successfully!', 'success');
        } else {
          showToast('Failed to save quotation', 'error');
        }
      }
    });

    // Initialize
    initDataSdk();
    updateBusinessDisplay();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9cabad8354925138',t:'MTc3MDU1OTQ4My4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
