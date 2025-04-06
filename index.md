<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CFP Financial Planner Pro</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        .sidebar {
            transition: all 0.3s;
        }
        .sidebar.collapsed {
            width: 70px;
        }
        .sidebar.collapsed .sidebar-text {
            display: none;
        }
        .sidebar.collapsed .logo-text {
            display: none;
        }
        .sidebar.collapsed .nav-item {
            justify-content: center;
        }
        .chart-container {
            height: 300px;
        }
        .input-highlight {
            transition: all 0.2s;
        }
        .input-highlight:focus {
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        .progress-bar {
            transition: width 0.6s ease;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
            animation: fadeIn 0.3s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .tooltip {
            position: relative;
        }
        .tooltip-text {
            visibility: hidden;
            width: 200px;
            background-color: #333;
            color: #fff;
            text-align: center;
            border-radius: 6px;
            padding: 5px;
            position: absolute;
            z-index: 1;
            bottom: 125%;
            left: 50%;
            transform: translateX(-50%);
            opacity: 0;
            transition: opacity 0.3s;
        }
        .tooltip:hover .tooltip-text {
            visibility: visible;
            opacity: 1;
        }
    </style>
</head>
<body class="bg-gray-100 font-sans">
    <div class="flex h-screen overflow-hidden">
        <!-- Sidebar -->
        <div class="sidebar bg-blue-800 text-white w-64 flex-shrink-0 flex flex-col">
            <div class="p-4 flex items-center border-b border-blue-700">
                <div class="w-10 h-10 rounded-full bg-blue-600 flex items-center justify-center">
                    <i class="fas fa-piggy-bank text-xl"></i>
                </div>
                <span class="logo-text ml-3 text-xl font-bold">CFP Planner Pro</span>
            </div>
            <div class="flex-1 overflow-y-auto">
                <nav class="p-4">
                    <div class="space-y-2">
                        <a href="#" class="nav-item flex items-center px-4 py-3 rounded-lg bg-blue-700 text-white">
                            <i class="fas fa-home"></i>
                            <span class="sidebar-text ml-3">Dashboard</span>
                        </a>
                        <a href="#" class="nav-item flex items-center px-4 py-3 rounded-lg hover:bg-blue-700 text-white">
                            <i class="fas fa-user"></i>
                            <span class="sidebar-text ml-3">Client Profile</span>
                        </a>
                        <a href="#" class="nav-item flex items-center px-4 py-3 rounded-lg hover:bg-blue-700 text-white">
                            <i class="fas fa-chart-line"></i>
                            <span class="sidebar-text ml-3">Cash Flow</span>
                        </a>
                        <a href="#" class="nav-item flex items-center px-4 py-3 rounded-lg hover:bg-blue-700 text-white">
                            <i class="fas fa-umbrella-beach"></i>
                            <span class="sidebar-text ml-3">Retirement</span>
                        </a>
                        <a href="#" class="nav-item flex items-center px-4 py-3 rounded-lg hover:bg-blue-700 text-white">
                            <i class="fas fa-file-invoice-dollar"></i>
                            <span class="sidebar-text ml-3">Tax Planning</span>
                        </a>
                        <a href="#" class="nav-item flex items-center px-4 py-3 rounded-lg hover:bg-blue-700 text-white">
                            <i class="fas fa-shield-alt"></i>
                            <span class="sidebar-text ml-3">Risk Analysis</span>
                        </a>
                        <a href="#" class="nav-item flex items-center px-4 py-3 rounded-lg hover:bg-blue-700 text-white">
                            <i class="fas fa-cog"></i>
                            <span class="sidebar-text ml-3">Settings</span>
                        </a>
                    </div>
                </nav>
            </div>
            <div class="p-4 border-t border-blue-700">
                <button class="flex items-center justify-center w-full py-2 rounded-lg bg-blue-700 text-white">
                    <i class="fas fa-sign-out-alt"></i>
                    <span class="sidebar-text ml-3">Logout</span>
                </button>
            </div>
        </div>
        <!-- Main Content -->
        <div class="flex-1 overflow-auto">
            <!-- Top Navigation -->
            <header class="bg-white shadow-sm">
                <div class="px-6 py-4 flex items-center justify-between">
                    <div class="flex items-center">
                        <button id="sidebarToggle" class="mr-4 text-gray-500 hover:text-gray-700">
                            <i class="fas fa-bars text-xl"></i>
                        </button>
                        <h1 class="text-xl font-semibold text-gray-800">Client Financial Plan</h1>
                    </div>
                    <div class="flex items-center space-x-4">
                        <div class="relative">
                            <input type="text" placeholder="Search..." class="pl-10 pr-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500">
                            <i class="fas fa-search absolute left-3 top-3 text-gray-400"></i>
                        </div>
                        <div class="relative">
                            <i class="fas fa-bell text-xl text-gray-500 hover:text-blue-600 cursor-pointer"></i>
                            <span class="absolute top-0 right-0 w-2 h-2 bg-red-500 rounded-full"></span>
                        </div>
                        <div class="flex items-center">
                            <div class="w-8 h-8 rounded-full bg-blue-600 flex items-center justify-center text-white">
                                <span>JD</span>
                            </div>
                            <span class="ml-2 text-sm font-medium">John Doe</span>
                        </div>
                    </div>
                </div>
            </header>
            <!-- Client Info Bar -->
            <div class="bg-blue-50 px-6 py-3 border-b">
                <div class="flex items-center justify-between">
                    <div class="flex items-center space-x-4">
                        <div class="w-12 h-12 rounded-full bg-blue-100 flex items-center justify-center">
                            <i class="fas fa-user text-blue-600"></i>
                        </div>
                        <div>
                            <h2 class="font-semibold text-gray-800">Sarah Johnson</h2>
                            <p class="text-sm text-gray-600">Client since 2018</p>
                        </div>
                    </div>
                    <div class="flex items-center space-x-6">
                        <div class="text-center">
                            <p class="text-xs text-gray-500">Age</p>
                            <p class="font-medium">42</p>
                        </div>
                        <div class="text-center">
                            <p class="text-xs text-gray-500">Income</p>
                            <p class="font-medium">$125,000</p>
                        </div>
                        <div class="text-center">
                            <p class="text-xs text-gray-500">Net Worth</p>
                            <p class="font-medium">$850,000</p>
                        </div>
                        <div class="text-center">
                            <p class="text-xs text-gray-500">Risk Score</p>
                            <p class="font-medium">Moderate</p>
                        </div>
                    </div>
                    <div>
                        <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 flex items-center">
                            <i class="fas fa-file-pdf mr-2"></i>
                            <span>Generate Report</span>
                        </button>
                    </div>
                </div>
            </div>
            <!-- Main Content Area -->
            <main class="p-6">
                <!-- Progress Steps -->
                <div class="mb-8">
                    <div class="flex justify-between items-center mb-4">
                        <h2 class="text-xl font-semibold text-gray-800">Financial Plan Progress</h2>
                        <span class="text-sm text-blue-600">65% Complete</span>
                    </div>
                    <div class="w-full bg-gray-200 rounded-full h-2.5">
                        <div class="progress-bar bg-blue-600 h-2.5 rounded-full" style="width: 65%"></div>
                    </div>
                    <div class="flex justify-between mt-2 text-sm text-gray-600">
                        <span>Data Collection</span>
                        <span>Analysis</span>
                        <span>Recommendations</span>
                        <span>Implementation</span>
                        <span>Review</span>
                    </div>
                </div>
                <!-- Tabs Navigation -->
                <div class="mb-6 border-b border-gray-200">
                    <ul class="flex flex-wrap -mb-px" id="planTabs">
                        <li class="mr-2">
                            <button class="tab-button inline-block p-4 border-b-2 border-blue-600 rounded-t-lg text-blue-600" data-tab="client-info">Client Info</button>
                        </li>
                        <li class="mr-2">
                            <button class="tab-button inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300" data-tab="cash-flow">Cash Flow</button>
                        </li>
                        <li class="mr-2">
                            <button class="tab-button inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300" data-tab="retirement">Retirement</button>
                        </li>
                        <li class="mr-2">
                            <button class="tab-button inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300" data-tab="tax-planning">Tax Planning</button>
                        </li>
                        <li class="mr-2">
                            <button class="tab-button inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300" data-tab="recommendations">Recommendations</button>
                        </li>
                    </ul>
                </div>
                <!-- Tab Content -->
                <div id="tabContent">
                    <!-- Client Info Tab -->
                    <div id="client-info" class="tab-content active">
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <!-- Personal Information -->
                            <div class="bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Personal Information</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div class="grid grid-cols-2 gap-4">
                                        <div>
                                            <label class="block text-sm font-medium text-gray-700 mb-1">First Name</label>
                                            <p class="text-gray-900">Sarah</p>
                                        </div>
                                        <div>
                                            <label class="block text-sm font-medium text-gray-700 mb-1">Last Name</label>
                                            <p class="text-gray-900">Johnson</p>
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Date of Birth</label>
                                        <p class="text-gray-900">June 15, 1981</p>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Marital Status</label>
                                        <p class="text-gray-900">Married</p>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Dependents</label>
                                        <p class="text-gray-900">2 children (ages 12 and 15)</p>
                                    </div>
                                </div>
                            </div>
                            <!-- Contact Information -->
                            <div class="bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Contact Information</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Address</label>
                                        <p class="text-gray-900">123 Financial Ave, Suite 100</p>
                                        <p class="text-gray-900">Boston, MA 02108</p>
                                    </div>
                                    <div class="grid grid-cols-2 gap-4">
                                        <div>
                                            <label class="block text-sm font-medium text-gray-700 mb-1">Phone</label>
                                            <p class="text-gray-900">(617) 555-0123</p>
                                        </div>
                                        <div>
                                            <label class="block text-sm font-medium text-gray-700 mb-1">Email</label>
                                            <p class="text-gray-900">sarah.johnson@example.com</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Financial Overview -->
                            <div class="bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Financial Overview</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div class="grid grid-cols-2 gap-4">
                                        <div>
                                            <label class="block text-sm font-medium text-gray-700 mb-1">Annual Income</label>
                                            <p class="text-gray-900">$125,000</p>
                                        </div>
                                        <div>
                                            <label class="block text-sm font-medium text-gray-700 mb-1">Net Worth</label>
                                            <p class="text-gray-900">$850,000</p>
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Primary Goals</label>
                                        <ul class="list-disc list-inside text-gray-900">
                                            <li>Retire by age 65</li>
                                            <li>Fund children's education</li>
                                            <li>Pay off mortgage in 15 years</li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                            <!-- Risk Profile -->
                            <div class="bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Risk Profile</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Risk Tolerance</label>
                                        <p class="text-gray-900">Moderate</p>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Time Horizon</label>
                                        <p class="text-gray-900">20+ years</p>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Liquidity Needs</label>
                                        <p class="text-gray-900">Moderate (3-6 months expenses)</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- Cash Flow Tab -->
                    <div id="cash-flow" class="tab-content">
                        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                            <!-- Income Section -->
                            <div class="lg:col-span-1 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Income</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-plus"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Salary</span>
                                            <span class="text-sm font-medium text-gray-900">$8,333/mo</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Primary employment</span>
                                            <span>$100,000 annual</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Bonus</span>
                                            <span class="text-sm font-medium text-gray-900">$2,083/mo</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Annual performance</span>
                                            <span>$25,000 annual</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Rental Income</span>
                                            <span class="text-sm font-medium text-gray-900">$1,500/mo</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Boston property</span>
                                            <span>$18,000 annual</span>
                                        </div>
                                    </div>
                                    <div class="pt-2">
                                        <div class="flex justify-between font-medium">
                                            <span class="text-gray-700">Total Income</span>
                                            <span class="text-blue-600">$11,916/mo</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Expenses Section -->
                            <div class="lg:col-span-1 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Expenses</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-plus"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Housing</span>
                                            <span class="text-sm font-medium text-gray-900">$2,500/mo</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Mortgage + utilities</span>
                                            <span>21% of income</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Transportation</span>
                                            <span class="text-sm font-medium text-gray-900">$800/mo</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Car payments + gas</span>
                                            <span>7% of income</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Food</span>
                                            <span class="text-sm font-medium text-gray-900">$1,200/mo</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Groceries + dining</span>
                                            <span>10% of income</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Education</span>
                                            <span class="text-sm font-medium text-gray-900">$500/mo</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Children's activities</span>
                                            <span>4% of income</span>
                                        </div>
                                    </div>
                                    <div class="pt-2">
                                        <div class="flex justify-between font-medium">
                                            <span class="text-gray-700">Total Expenses</span>
                                            <span class="text-red-600">$7,200/mo</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Cash Flow Analysis -->
                            <div class="lg:col-span-1 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Cash Flow Analysis</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-chart-pie"></i>
                                    </button>
                                </div>
                                <div class="space-y-6">
                                    <div>
                                        <div class="flex justify-between mb-2">
                                            <span class="text-sm font-medium text-gray-700">Monthly Net Cash Flow</span>
                                            <span class="text-sm font-medium text-green-600">$4,716</span>
                                        </div>
                                        <div class="w-full bg-gray-200 rounded-full h-2.5">
                                            <div class="bg-green-500 h-2.5 rounded-full" style="width: 60%"></div>
                                        </div>
                                        <p class="text-xs text-gray-500 mt-1">40% of income saved/invested</p>
                                    </div>
                                    <div>
                                        <h4 class="text-sm font-medium text-gray-700 mb-2">Expense Breakdown</h4>
                                        <div class="chart-container">
                                            <canvas id="expenseChart"></canvas>
                                        </div>
                                    </div>
                                    <div>
                                        <h4 class="text-sm font-medium text-gray-700 mb-2">Recommendations</h4>
                                        <ul class="space-y-2 text-sm text-gray-700">
                                            <li class="flex items-start">
                                                <i class="fas fa-check-circle text-green-500 mt-1 mr-2"></i>
                                                <span>Strong savings rate - consider increasing 401(k) contributions</span>
                                            </li>
                                            <li class="flex items-start">
                                                <i class="fas fa-exclamation-triangle text-yellow-500 mt-1 mr-2"></i>
                                                <span>Food expenses are 10% of income - could optimize to 8%</span>
                                            </li>
                                            <li class="flex items-start">
                                                <i class="fas fa-lightbulb text-blue-500 mt-1 mr-2"></i>
                                                <span>Consider refinancing mortgage at current lower rates</span>
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- Retirement Tab -->
                    <div id="retirement" class="tab-content">
                        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                            <!-- Retirement Accounts -->
                            <div class="lg:col-span-1 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Retirement Accounts</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-plus"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">401(k)</span>
                                            <span class="text-sm font-medium text-gray-900">$245,000</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Current employer</span>
                                            <span>8% contribution + 4% match</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Rollover IRA</span>
                                            <span class="text-sm font-medium text-gray-900">$112,000</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Previous employer</span>
                                            <span>60/40 stocks/bonds</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Roth IRA</span>
                                            <span class="text-sm font-medium text-gray-900">$48,000</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Annual contributions</span>
                                            <span>$6,000/year</span>
                                        </div>
                                    </div>
                                    <div class="pt-2">
                                        <div class="flex justify-between font-medium">
                                            <span class="text-gray-700">Total Retirement</span>
                                            <span class="text-blue-600">$405,000</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Retirement Projections -->
                            <div class="lg:col-span-2 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Retirement Projections</h3>
                                    <div class="flex space-x-2">
                                        <button class="px-3 py-1 bg-blue-600 text-white rounded hover:bg-blue-700 text-sm">
                                            Run Projection
                                        </button>
                                        <button class="px-3 py-1 border border-gray-300 rounded hover:bg-gray-50 text-sm">
                                            <i class="fas fa-sliders-h mr-1"></i>
                                            Adjust
                                        </button>
                                    </div>
                                </div>
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Retirement Age</label>
                                        <div class="flex items-center">
                                            <input type="range" min="60" max="75" value="65" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                                            <span class="ml-3 text-gray-900 font-medium">65</span>
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Annual Income Need</label>
                                        <div class="relative">
                                            <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                                <span class="text-gray-500">$</span>
                                            </div>
                                            <input type="text" class="pl-7 pr-12 py-2 border border-gray-300 rounded-md w-full" value="75,000">
                                            <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
                                                <span class="text-gray-500">/year</span>
                                            </div>
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Inflation Rate</label>
                                        <div class="relative">
                                            <input type="text" class="pr-10 py-2 border border-gray-300 rounded-md w-full" value="2.5">
                                            <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
                                                <span class="text-gray-500">%</span>
                                            </div>
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Investment Return</label>
                                        <div class="relative">
                                            <input type="text" class="pr-10 py-2 border border-gray-300 rounded-md w-full" value="6.5">
                                            <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
                                                <span class="text-gray-500">%</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                <div class="chart-container mb-6">
                                    <canvas id="retirementChart"></canvas>
                                </div>
                                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                                    <div class="bg-blue-50 p-4 rounded-lg">
                                        <p class="text-sm text-gray-600 mb-1">Projected Balance at 65</p>
                                        <p class="text-xl font-semibold text-blue-700">$1.42M</p>
                                    </div>
                                    <div class="bg-green-50 p-4 rounded-lg">
                                        <p class="text-sm text-gray-600 mb-1">Annual Withdrawal</p>
                                        <p class="text-xl font-semibold text-green-700">$75,000</p>
                                    </div>
                                    <div class="bg-purple-50 p-4 rounded-lg">
                                        <p class="text-sm text-gray-600 mb-1">Years Funded</p>
                                        <p class="text-xl font-semibold text-purple-700">28 years</p>
                                    </div>
                                </div>
                                <div class="mt-6 p-4 bg-yellow-50 rounded-lg">
                                    <div class="flex items-start">
                                        <i class="fas fa-exclamation-circle text-yellow-500 mt-1 mr-3"></i>
                                        <div>
                                            <h4 class="font-medium text-gray-800 mb-1">Recommendation</h4>
                                            <p class="text-sm text-gray-700">Based on current savings rate and projections, you may need to increase retirement contributions by $500/month to fully fund your retirement goals. Consider increasing 401(k) contributions to 10%.</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- Tax Planning Tab -->
                    <div id="tax-planning" class="tab-content">
                        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                            <!-- Current Year Tax Estimate -->
                            <div class="lg:col-span-1 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">2023 Tax Estimate</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-sync-alt"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Adjusted Gross Income</span>
                                            <span class="text-sm font-medium text-gray-900">$125,000</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Taxable Income</span>
                                            <span class="text-sm font-medium text-gray-900">$98,500</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">Federal Tax</span>
                                            <span class="text-sm font-medium text-gray-900">$17,200</span>
                                        </div>
                                        <div class="flex justify-between text-xs text-gray-500">
                                            <span>Effective rate: 13.8%</span>
                                            <span>Marginal rate: 22%</span>
                                        </div>
                                    </div>
                                    <div class="border-b pb-4">
                                        <div class="flex justify-between mb-1">
                                            <span class="text-sm font-medium text-gray-700">State Tax (MA)</span>
                                            <span class="text-sm font-medium text-gray-900">$5,125</span>
                                        </div>
                                        <div class="text-xs text-gray-500">
                                            <span>5.0% flat rate</span>
                                        </div>
                                    </div>
                                    <div class="pt-2">
                                        <div class="flex justify-between font-medium">
                                            <span class="text-gray-700">Total Tax Liability</span>
                                            <span class="text-red-600">$22,325</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Tax Reduction Strategies -->
                            <div class="lg:col-span-1 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Tax Reduction Strategies</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-plus"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div class="p-3 bg-blue-50 rounded-lg">
                                        <div class="flex items-start">
                                            <div class="flex-shrink-0 mt-1">
                                                <i class="fas fa-hand-holding-usd text-blue-500"></i>
                                            </div>
                                            <div class="ml-3">
                                                <h4 class="text-sm font-medium text-blue-800">Maximize 401(k)</h4>
                                                <p class="text-xs text-gray-600 mt-1">Increase contributions to $22,500 limit. Potential savings: $4,950</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="p-3 bg-green-50 rounded-lg">
                                        <div class="flex items-start">
                                            <div class="flex-shrink-0 mt-1">
                                                <i class="fas fa-home text-green-500"></i>
                                            </div>
                                            <div class="ml-3">
                                                <h4 class="text-sm font-medium text-green-800">Mortgage Interest</h4>
                                                <p class="text-xs text-gray-600 mt-1">Itemize deductions. Potential savings: $1,200</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="p-3 bg-purple-50 rounded-lg">
                                        <div class="flex items-start">
                                            <div class="flex-shrink-0 mt-1">
                                                <i class="fas fa-graduation-cap text-purple-500"></i>
                                            </div>
                                            <div class="ml-3">
                                                <h4 class="text-sm font-medium text-purple-800">529 Contributions</h4>
                                                <p class="text-xs text-gray-600 mt-1">State tax deduction up to $2,000. Potential savings: $100</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="p-3 bg-yellow-50 rounded-lg">
                                        <div class="flex items-start">
                                            <div class="flex-shrink-0 mt-1">
                                                <i class="fas fa-heart text-yellow-500"></i>
                                            </div>
                                            <div class="ml-3">
                                                <h4 class="text-sm font-medium text-yellow-800">Charitable Giving</h4>
                                                <p class="text-xs text-gray-600 mt-1">Donor-advised fund. Potential savings: varies</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="p-3 bg-red-50 rounded-lg">
                                        <div class="flex items-start">
                                            <div class="flex-shrink-0 mt-1">
                                                <i class="fas fa-procedures text-red-500"></i>
                                            </div>
                                            <div class="ml-3">
                                                <h4 class="text-sm font-medium text-red-800">HSA Contributions</h4>
                                                <p class="text-xs text-gray-600 mt-1">$3,850 family limit. Potential savings: $847</p>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Tax Projection Calculator -->
                            <div class="lg:col-span-1 bg-white p-6 rounded-lg shadow-sm">
                                <div class="flex justify-between items-center mb-4">
                                    <h3 class="text-lg font-medium text-gray-800">Tax Projection Calculator</h3>
                                    <button class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-calculator"></i>
                                    </button>
                                </div>
                                <div class="space-y-4">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Filing Status</label>
                                        <select class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md">
                                            <option>Single</option>
                                            <option selected>Married Filing Jointly</option>
                                            <option>Head of Household</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Projected Income</label>
                                        <div class="relative">
                                            <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                                <span class="text-gray-500">$</span>
                                            </div>
                                            <input type="text" class="pl-7 pr-12 py-2 border border-gray-300 rounded-md w-full" value="125,000">
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Pre-tax Deductions</label>
                                        <div class="relative">
                                            <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                                <span class="text-gray-500">$</span>
                                            </div>
                                            <input type="text" class="pl-7 pr-12 py-2 border border-gray-300 rounded-md w-full" value="18,000">
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Itemized Deductions</label>
                                        <div class="relative">
                                            <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                                <span class="text-gray-500">$</span>
                                            </div>
                                            <input type="text" class="pl-7 pr-12 py-2 border border-gray-300 rounded-md w-full" value="15,000">
                                        </div>
                                    </div>
                                    <div class="pt-2">
                                        <button class="w-full bg-blue-600 text-white py-2 px-4 rounded-md hover:bg-blue-700">
                                            Calculate Projection
                                        </button>
                                    </div>
                                    <div class="mt-4 p-3 bg-gray-50 rounded-lg">
                                        <div class="flex justify-between">
                                            <span class="text-sm font-medium text-gray-700">Projected Tax</span>
                                            <span class="text-sm font-medium text-gray-900">$21,450</span>
                                        </div>
                                        <div class="flex justify-between mt-1">
                                            <span class="text-xs text-gray-500">Effective Rate</span>
                                            <span class="text-xs text-gray-500">17.2%</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- Recommendations Tab -->
                    <div id="recommendations" class="tab-content">
                        <div class="bg-white p-6 rounded-lg shadow-sm">
                            <div class="flex justify-between items-center mb-6">
                                <h3 class="text-lg font-medium text-gray-800">Financial Plan Recommendations</h3>
                                <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 flex items-center">
                                    <i class="fas fa-check-circle mr-2"></i>
                                    <span>Accept All</span>
                                </button>
                            </div>    
                            <div class="space-y-6">
                                <!-- Retirement Recommendation -->
                                <div class="border border-gray-200 rounded-lg overflow-hidden">
                                    <div class="bg-gray-50 px-4 py-3 flex justify-between items-center">
                                        <div class="flex items-center">
                                            <div class="w-8 h-8 rounded-full bg-blue-100 flex items-center justify-center mr-3">
                                                <i class="fas fa-umbrella-beach text-blue-600"></i>
                                            </div>
                                            <h4 class="font-medium text-gray-800">Retirement Planning</h4>
                                        </div>
                                        <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-blue-100 text-blue-800">
                                            High Priority
                                        </span>
                                    </div>
                                    <div class="p-4">
                                        <p class="text-gray-700 mb-4">Based on your current savings rate and retirement goals, we recommend increasing your retirement contributions to ensure adequate funding for your desired retirement lifestyle.</p>
                                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-4">
                                            <div class="border-l-4 border-blue-500 pl-3">
                                                <p class="text-sm text-gray-500">Current Contribution</p>
                                                <p class="font-medium">$1,000/month</p>
                                            </div>
                                            <div class="border-l-4 border-green-500 pl-3">
                                                <p class="text-sm text-gray-500">Recommended</p>
                                                <p class="font-medium text-green-600">$1,500/month</p>
                                            </div>
                                            <div class="border-l-4 border-purple-500 pl-3">
                                                <p class="text-sm text-gray-500">Impact</p>
                                                <p class="font-medium">+$250k at retirement</p>
                                            </div>
                                        </div>
                                        <div class="flex space-x-3">
                                            <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
                                                Accept
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Modify
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Decline
                                            </button>
                                        </div>
                                    </div>
                                </div>           
                                <!-- Tax Recommendation -->
                                <div class="border border-gray-200 rounded-lg overflow-hidden">
                                    <div class="bg-gray-50 px-4 py-3 flex justify-between items-center">
                                        <div class="flex items-center">
                                            <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center mr-3">
                                                <i class="fas fa-file-invoice-dollar text-green-600"></i>
                                            </div>
                                            <h4 class="font-medium text-gray-800">Tax Optimization</h4>
                                        </div>
                                        <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800">
                                            Medium Priority
                                        </span>
                                    </div>
                                    <div class="p-4">
                                        <p class="text-gray-700 mb-4">You have opportunities to reduce your tax liability through increased retirement contributions and taking advantage of available deductions.</p>
                                        <div class="mb-4">
                                            <div class="flex items-center justify-between mb-1">
                                                <span class="text-sm font-medium text-gray-700">Maximize 401(k) Contributions</span>
                                                <span class="text-sm font-medium text-green-600">Potential savings: $4,950</span>
                                            </div>
                                            <div class="w-full bg-gray-200 rounded-full h-2">
                                                <div class="bg-green-500 h-2 rounded-full" style="width: 70%"></div>
                                            </div>
                                        </div>
                                        <div class="mb-4">
                                            <div class="flex items-center justify-between mb-1">
                                                <span class="text-sm font-medium text-gray-700">HSA Contributions</span>
                                                <span class="text-sm font-medium text-blue-600">Potential savings: $847</span>
                                            </div>
                                            <div class="w-full bg-gray-200 rounded-full h-2">
                                                <div class="bg-blue-500 h-2 rounded-full" style="width: 30%"></div>
                                            </div>
                                        </div>
                                        <div class="flex space-x-3">
                                            <button class="px-4 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700">
                                                Accept
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Modify
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Decline
                                            </button>
                                        </div>
                                    </div>
                                </div>
                                <!-- Education Recommendation -->
                                <div class="border border-gray-200 rounded-lg overflow-hidden">
                                    <div class="bg-gray-50 px-4 py-3 flex justify-between items-center">
                                        <div class="flex items-center">
                                            <div class="w-8 h-8 rounded-full bg-purple-100 flex items-center justify-center mr-3">
                                                <i class="fas fa-graduation-cap text-purple-600"></i>
                                            </div>
                                            <h4 class="font-medium text-gray-800">Education Funding</h4>
                                        </div>
                                        <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-purple-100 text-purple-800">
                                            Medium Priority
                                        </span>
                                    </div>
                                    <div class="p-4">
                                        <p class="text-gray-700 mb-4">To meet your goal of funding your children's college education, we recommend establishing 529 plans and contributing regularly.</p>
                                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                                            <div>
                                                <label class="block text-sm font-medium text-gray-700 mb-1">Child 1 (Age 15)</label>
                                                <div class="relative">
                                                    <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                                        <span class="text-gray-500">$</span>
                                                    </div>
                                                    <input type="text" class="pl-7 pr-12 py-2 border border-gray-300 rounded-md w-full" value="250">
                                                    <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
                                                        <span class="text-gray-500">/month</span>
                                                    </div>
                                                </div>
                                            </div>
                                            <div>
                                                <label class="block text-sm font-medium text-gray-700 mb-1">Child 2 (Age 12)</label>
                                                <div class="relative">
                                                    <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                                        <span class="text-gray-500">$</span>
                                                    </div>
                                                    <input type="text" class="pl-7 pr-12 py-2 border border-gray-300 rounded-md w-full" value="300">
                                                    <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
                                                        <span class="text-gray-500">/month</span>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="flex space-x-3">
                                            <button class="px-4 py-2 bg-purple-600 text-white rounded-lg hover:bg-purple-700">
                                                Accept
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Modify
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Decline
                                            </button>
                                        </div>
                                    </div>
                                </div> 
                                <!-- Insurance Recommendation -->
                                <div class="border border-gray-200 rounded-lg overflow-hidden">
                                    <div class="bg-gray-50 px-4 py-3 flex justify-between items-center">
                                        <div class="flex items-center">
                                            <div class="w-8 h-8 rounded-full bg-red-100 flex items-center justify-center mr-3">
                                                <i class="fas fa-shield-alt text-red-600"></i>
                                            </div>
                                            <h4 class="font-medium text-gray-800">Insurance Review</h4>
                                        </div>
                                        <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-red-100 text-red-800">
                                            Low Priority
                                        </span>
                                    </div>
                                    <div class="p-4">
                                        <p class="text-gray-700 mb-4">Your current life insurance coverage may be insufficient to protect your family's financial needs. We recommend reviewing your policies.</p>
                                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                                            <div>
                                                <label class="block text-sm font-medium text-gray-700 mb-1">Current Coverage</label>
                                                <p class="text-gray-900">$500,000 term life</p>
                                            </div>
                                            <div>
                                                <label class="block text-sm font-medium text-gray-700 mb-1">Recommended Coverage</label>
                                                <p class="text-red-600 font-medium">$1,000,000 term life</p>
                                            </div>
                                        </div>
                                        <div class="flex space-x-3">
                                            <button class="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700">
                                                Accept
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Modify
                                            </button>
                                            <button class="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50">
                                                Decline
                                            </button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </main>
        </div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // Tab functionality
        document.addEventListener('DOMContentLoaded', function() {
            const tabButtons = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    // Remove active class from all buttons and contents
                    tabButtons.forEach(btn => btn.classList.remove('border-blue-600', 'text-blue-600'));
                    tabButtons.forEach(btn => btn.classList.add('border-transparent', 'hover:text-gray-600', 'hover:border-gray-300'));
                    tabContents.forEach(content => content.classList.remove('active'));
                    // Add active class to clicked button and corresponding content
                    this.classList.remove('border-transparent', 'hover:text-gray-600', 'hover:border-gray-300');
                    this.classList.add('border-blue-600', 'text-blue-600');
                    document.getElementById(tabId).classList.add('active');
                });
            });
            // Sidebar toggle
            const sidebarToggle = document.getElementById('sidebarToggle');
            const sidebar = document.querySelector('.sidebar');
            sidebarToggle.addEventListener('click', function() {
                sidebar.classList.toggle('collapsed');
            });
            // Expense Chart
            const expenseCtx = document.getElementById('expenseChart').getContext('2d');
            const expenseChart = new Chart(expenseCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Housing', 'Transportation', 'Food', 'Education', 'Entertainment', 'Savings'],
                    datasets: [{
                        data: [2500, 800, 1200, 500, 400, 1800],
                        backgroundColor: [
                            '#3B82F6',
                            '#10B981',
                            '#F59E0B',
                            '#6366F1',
                            '#EC4899',
                            '#64748B'
                        ],
                        borderWidth: 0
                    }]
                },
                options: {
                    cutout: '70%',
                    plugins: {
                        legend: {
                            position: 'right',
                            labels: {
                                boxWidth: 10,
                                padding: 15
                            }
                        }
                    }
                }
            });
            // Retirement Chart
            const retirementCtx = document.getElementById('retirementChart').getContext('2d');
            const retirementChart = new Chart(retirementCtx, {
                type: 'line',
                data: {
                    labels: ['Current', '50', '55', '60', '65', '70', '75', '80', '85', '90'],
                    datasets: [
                        {
                            label: 'Projected Balance',
                            data: [405000, 650000, 920000, 1240000, 1420000, 1180000, 920000, 650000, 380000, 100000],
                            borderColor: '#3B82F6',
                            backgroundColor: 'rgba(59, 130, 246, 0.05)',
                            fill: true,
                            tension: 0.4
                        },
                        {
                            label: 'Withdrawals Start',
                            data: [null, null, null, null, 1420000, 1180000, 920000, 650000, 380000, 100000],
                            borderColor: '#10B981',
                            backgroundColor: 'rgba(16, 185, 129, 0.05)',
                            fill: true,
                            tension: 0.4
                        }
                    ]
                },
                options: {
                    responsive: true,
                    plugins: {
                        tooltip: {
                            mode: 'index',
                            intersect: false,
                        },
                        legend: {
                            position: 'top',
                        }
                    },
                    scales: {
                        y: {
                            beginAtZero: false,
                            ticks: {
                                callback: function(value) {
                                    return '$' + (value / 1000) + 'k';
                                }
                            }
                        }
                    }
                }
            });
        });
    </script>
</body>
</html>
