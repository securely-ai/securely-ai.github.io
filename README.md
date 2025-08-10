<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Expresso Post - Delivering Confidence Since 1995</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Montserrat:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body { font-family: 'Inter', sans-serif; }
        .font-montserrat { font-family: 'Montserrat', sans-serif; }
    </style>
</head>
<body class="min-h-screen bg-white text-gray-900 antialiased">
    <!-- Header -->
    <header class="bg-gradient-to-r from-blue-900 to-blue-800 text-white">
        <div class="max-w-7xl mx-auto px-6 py-6 flex items-center justify-between">
            <div class="flex items-center gap-4">
                <div class="bg-white/10 p-2 rounded-md">
                    <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 17l4 4 4-4m-4-5v9"/>
                    </svg>
                </div>
                <div>
                    <h1 class="font-montserrat text-2xl font-bold">Expresso Post</h1>
                    <p class="text-sm text-white/90">Delivering Confidence Since 1995</p>
                </div>
            </div>

            <nav class="hidden md:flex items-center gap-6 text-sm">
                <a href="#features" class="hover:underline">Services</a>
                <a href="#track" class="hover:underline">Track</a>
                <a href="#terms" class="hover:underline">Terms</a>
                <a href="#contact" class="hover:underline">Contact</a>
                <button class="px-4 py-2 bg-yellow-400 text-blue-900 rounded-md font-semibold hover:bg-yellow-300 transition-colors">
                    Get Quote
                </button>
            </nav>

            <!-- Mobile menu button -->
            <button class="md:hidden p-2" onclick="toggleMobileMenu()">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
                </svg>
            </button>
        </div>

        <!-- Mobile menu -->
        <div id="mobileMenu" class="hidden md:hidden bg-blue-800 px-6 py-4">
            <nav class="flex flex-col gap-4 text-sm">
                <a href="#features" class="hover:underline">Services</a>
                <a href="#track" class="hover:underline">Track</a>
                <a href="#terms" class="hover:underline">Terms</a>
                <a href="#contact" class="hover:underline">Contact</a>
                <button class="px-4 py-2 bg-yellow-400 text-blue-900 rounded-md font-semibold w-fit">
                    Get Quote
                </button>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="bg-gradient-to-br from-blue-50 to-indigo-100 py-20">
        <div class="max-w-7xl mx-auto px-6 text-center">
            <h2 class="font-montserrat text-5xl md:text-6xl font-bold text-gray-900 mb-6">
                Lightning-Fast Delivery
            </h2>
            <p class="text-xl text-gray-600 mb-8 max-w-2xl mx-auto">
                Experience the future of shipping with our 99.97% on-time delivery rate and real-time tracking technology.
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                <button class="px-8 py-4 bg-blue-900 text-white rounded-lg font-semibold hover:bg-blue-800 transition-colors">
                    Ship Now
                </button>
                <button class="px-8 py-4 border-2 border-blue-900 text-blue-900 rounded-lg font-semibold hover:bg-blue-900 hover:text-white transition-colors">
                    Learn More
                </button>
            </div>
        </div>
    </section>

    <!-- Tracking Section -->
    <section id="track" class="py-16 bg-white">
        <div class="max-w-4xl mx-auto px-6">
            <div class="text-center mb-12">
                <h3 class="font-montserrat text-3xl font-bold text-gray-900 mb-4">Track Your Package</h3>
                <p class="text-gray-600">Enter your tracking ID to get real-time updates</p>
            </div>

            <div class="bg-gray-50 rounded-xl p-8">
                <form onsubmit="handleTrack(event)" class="mb-8">
                    <div class="flex flex-col sm:flex-row gap-4">
                        <input 
                            type="text" 
                            id="trackingInput"
                            placeholder="Enter tracking ID (e.g., EXP-1995-TX-A1B2)"
                            class="flex-1 px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                        >
                        <button 
                            type="submit"
                            class="px-8 py-3 bg-blue-900 text-white rounded-lg font-semibold hover:bg-blue-800 transition-colors"
                        >
                            Track Package
                        </button>
                    </div>
                </form>



                <!-- Tracking Results -->
                <div id="trackingResults" class="hidden">
                    <div class="bg-white rounded-lg p-6 border border-gray-200">
                        <div class="flex items-center justify-between mb-4">
                            <h4 class="font-semibold text-lg">Package Status</h4>
                            <span id="trackingId" class="text-sm text-gray-500"></span>
                        </div>
                        
                        <div class="grid md:grid-cols-2 gap-6 mb-6">
                            <div>
                                <div class="mb-4">
                                    <div class="flex items-center gap-3 mb-2">
                                        <div id="statusIcon" class="w-3 h-3 rounded-full bg-green-500"></div>
                                        <span id="packageStatus" class="font-semibold text-green-700"></span>
                                    </div>
                                    <p class="text-gray-600 text-sm">
                                        ETA: <span id="packageEta"></span>
                                    </p>
                                    <p class="text-gray-600 text-sm">
                                        Location: <span id="packageLocation"></span>
                                    </p>
                                </div>

                                <div class="grid grid-cols-2 gap-4 text-sm">
                                    <div>
                                        <p class="text-gray-500">Carbon Impact</p>
                                        <p class="font-semibold"><span id="carbonImpact"></span> kg CO₂</p>
                                    </div>
                                    <div>
                                        <p class="text-gray-500">Delay Risk</p>
                                        <p id="delayRisk" class="font-semibold"></p>
                                    </div>
                                </div>
                            </div>

                            <div>
                                <p class="text-gray-500 text-sm mb-2">Last Updated</p>
                                <p id="lastUpdated" class="text-sm"></p>
                            </div>
                        </div>

                        <div class="text-center">
                            <button 
                                onclick="showDetailedTracking()"
                                class="px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors text-sm font-medium"
                            >
                                View Detailed Tracking
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Detailed Tracking Modal -->
                <div id="detailedTrackingModal" class="hidden fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center p-4">
                    <div class="bg-white rounded-xl max-w-4xl w-full max-h-[90vh] overflow-y-auto">
                        <div class="p-6">
                            <div class="flex items-center justify-between mb-6">
                                <h1 class="text-2xl font-bold">Shipment Tracking</h1>
                                <button onclick="closeDetailedTracking()" class="text-gray-500 hover:text-gray-700">
                                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                                    </svg>
                                </button>
                            </div>

                            <div class="grid md:grid-cols-2 gap-8">
                                <!-- Left Column -->
                                <div>
                                    <div class="mb-6">
                                        <div class="bg-gray-50 p-4 rounded-lg">
                                            <p class="mb-2"><strong>Tracking ID:</strong> <span id="detailedTrackingId">EXP-1995-TX-HN79</span></p>
                                            <p class="mb-2"><strong>Route:</strong> Canada → United States</p>
                                            <p class="mb-2"><strong>Date Shipped:</strong> August 2, 2025</p>
                                            <p class="mb-2"><strong>Estimated Delivery:</strong> August 15, 2025</p>
                                            <p class="mb-2"><strong>Current Date:</strong> August 9, 2025</p>
                                            <p><strong>Status:</strong> <span class="text-blue-600 font-semibold">In USA — Undergoing Customs Clearance</span></p>
                                        </div>
                                    </div>

                                    <div class="mb-6">
                                        <h2 class="text-xl font-semibold mb-3 text-gray-800 flex items-center gap-2">
                                            <svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
                                            </svg>
                                            Recipient
                                        </h2>
                                        <div class="bg-green-50 p-4 rounded-lg border-l-4 border-green-400">
                                            <p class="font-semibold">Donal Davis</p>
                                            <p class="text-gray-600">1st Street Austin 433</p>
                                        </div>
                                    </div>

                                    <div class="mb-6">
                                        <h2 class="text-xl font-semibold mb-3 text-gray-800 flex items-center gap-2">
                                            <svg class="w-5 h-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"/>
                                            </svg>
                                            Sender
                                        </h2>
                                        <div class="bg-blue-50 p-4 rounded-lg border-l-4 border-blue-400">
                                            <p class="font-semibold">Tony Montana</p>
                                            <p class="text-gray-600">Canada, Ontario</p>
                                        </div>
                                    </div>

                                    <div class="mb-6">
                                        <h2 class="text-xl font-semibold mb-3 text-gray-800 flex items-center gap-2">
                                            <svg class="w-5 h-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/>
                                            </svg>
                                            Tracking Timeline
                                        </h2>
                                        <div class="bg-blue-50 p-4 rounded-lg border-l-4 border-blue-400">
                                            <div class="space-y-3">
                                                <div class="flex items-center gap-3">
                                                    <div class="w-3 h-3 bg-green-500 rounded-full"></div>
                                                    <div>
                                                        <p class="font-semibold text-green-700">Picked Up</p>
                                                        <p class="text-sm text-gray-600">August 3, 2025 - Package collected from sender</p>
                                                    </div>
                                                </div>
                                                <div class="flex items-center gap-3">
                                                    <div class="w-3 h-3 bg-green-500 rounded-full"></div>
                                                    <div>
                                                        <p class="font-semibold text-green-700">Shipped</p>
                                                        <p class="text-sm text-gray-600">August 4, 2025 - Departed from Canada facility</p>
                                                    </div>
                                                </div>
                                                <div class="flex items-center gap-3">
                                                    <div class="w-3 h-3 bg-green-500 rounded-full"></div>
                                                    <div>
                                                        <p class="font-semibold text-green-700">Arrived at Port</p>
                                                        <p class="text-sm text-gray-600">August 7, 2025 - Arrived at US port facility</p>
                                                    </div>
                                                </div>
                                                <div class="flex items-center gap-3">
                                                    <div class="w-3 h-3 bg-yellow-500 rounded-full animate-pulse"></div>
                                                    <div>
                                                        <p class="font-semibold text-yellow-700">At Customs</p>
                                                        <p class="text-sm text-gray-600">August 9, 2025 - Awaiting customs payment and clearance</p>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                    <div class="mb-6">
                                        <h2 class="text-xl font-semibold mb-3 text-gray-800 flex items-center gap-2">
                                            <svg class="w-5 h-5 text-yellow-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1"/>
                                            </svg>
                                            Customs Information
                                        </h2>
                                        <div class="bg-yellow-50 p-4 rounded-lg border-l-4 border-yellow-400">
                                            <p class="mb-2"><strong>Customs Fee:</strong> <span class="text-2xl font-bold text-green-600">$2,340</span></p>
                                            <p class="text-sm text-gray-600">Please check your email for the customs invoice from <em>Proton Express Delivery</em>.</p>
                                        </div>
                                    </div>
                                </div>

                                <!-- Right Column -->
                                <div>
                                    <div class="mb-6">
                                        <h2 class="text-xl font-semibold mb-3 text-gray-800 flex items-center gap-2">
                                            <svg class="w-5 h-5 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7v8a2 2 0 002 2h6M8 7V5a2 2 0 012-2h4.586a1 1 0 01.707.293l4.414 4.414a1 1 0 01.293.707V15a2 2 0 01-2 2h-2M8 7H6a2 2 0 00-2 2v10a2 2 0 002 2h8a2 2 0 002-2v-2"/>
                                            </svg>
                                            Delivery Item
                                        </h2>
                                        <div class="bg-gray-50 p-4 rounded-lg">
                                            <div class="flex items-center gap-3 mb-4">
                                                <div class="w-16 h-12 bg-gray-200 rounded-lg overflow-hidden">
                                                    <img src="https://imgur.com/Mlpq8k0.jpg" alt="Mercedes-Benz C250" class="w-full h-full object-cover" onerror="this.src=''; this.alt='Car image failed to load'; this.style.display='none';">
                                                </div>
                                                <div>
                                                    <p class="text-xl font-bold">Mercedes-Benz C-Class C 250</p>
                                                    <p class="text-gray-600">2012 Model Year</p>
                                                    <p class="text-lg font-bold text-green-600">$25,500</p>
                                                </div>
                                            </div>
                                            <div class="grid grid-cols-2 gap-4 text-sm">
                                                <div>
                                                    <p class="text-gray-500">Condition</p>
                                                    <p class="font-semibold text-green-600">Brand New</p>
                                                </div>
                                                <div>
                                                    <p class="text-gray-500">Color</p>
                                                    <p class="font-semibold">Black</p>
                                                </div>
                                                <div class="col-span-2">
                                                    <p class="text-gray-500">VIN</p>
                                                    <p class="font-mono text-sm bg-white p-2 rounded border">WDDGF4HB8CA652315</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                    <div class="mb-6">
                                        <h2 class="text-xl font-semibold mb-3 text-gray-800 flex items-center gap-2">
                                            <svg class="w-5 h-5 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"/>
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
                                            </svg>
                                            Vehicle Specifications
                                        </h2>
                                        <div class="bg-gray-50 p-4 rounded-lg">
                                            <div class="grid grid-cols-1 gap-2 text-sm">
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Engine:</span>
                                                    <span class="font-semibold">3.0L V6</span>
                                                </div>
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Transmission:</span>
                                                    <span class="font-semibold">7-Speed Automatic</span>
                                                </div>
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Horsepower:</span>
                                                    <span class="font-semibold">228 hp</span>
                                                </div>
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Drivetrain:</span>
                                                    <span class="font-semibold">Rear-Wheel Drive</span>
                                                </div>
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Fuel Type:</span>
                                                    <span class="font-semibold">Gasoline</span>
                                                </div>
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Seating:</span>
                                                    <span class="font-semibold">5 Passengers</span>
                                                </div>
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Interior:</span>
                                                    <span class="font-semibold">Leather Upholstery</span>
                                                </div>
                                                <div class="flex justify-between py-1 border-b border-gray-200">
                                                    <span class="text-gray-600">Infotainment:</span>
                                                    <span class="font-semibold">Premium Audio, Navigation</span>
                                                </div>
                                                <div class="flex justify-between py-1">
                                                    <span class="text-gray-600">Safety:</span>
                                                    <span class="font-semibold">ABS, Airbags, Stability Control</span>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div class="mt-8 pt-6 border-t border-gray-200">
                                <div class="flex flex-col sm:flex-row gap-4 justify-center">
                                    <button onclick="closeDetailedTracking()" class="px-6 py-2 bg-gray-500 text-white rounded-lg hover:bg-gray-600 transition-colors">
                                        Close
                                    </button>
                                    <button class="px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors">
                                        Download Invoice
                                    </button>
                                    <button class="px-6 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 transition-colors">
                                        Contact Support
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Performance Metrics -->
    <section class="py-16 bg-gray-50">
        <div class="max-w-6xl mx-auto px-6">
            <div class="text-center mb-12">
                <h3 class="font-montserrat text-3xl font-bold text-gray-900 mb-4">Our Performance</h3>
                <p class="text-gray-600">Industry-leading delivery statistics</p>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <!-- On-time Rate Chart -->
                <div class="bg-white rounded-xl p-6 text-center">
                    <h4 class="font-semibold text-lg mb-4">On-Time Delivery</h4>
                    <div class="w-32 h-32 mx-auto mb-4">
                        <canvas id="onTimeChart"></canvas>
                    </div>
                    <p class="text-3xl font-bold text-green-600">99.97%</p>
                    <p class="text-gray-500 text-sm">Packages delivered on time</p>
                </div>

                <!-- Customer Rating -->
                <div class="bg-white rounded-xl p-6 text-center">
                    <h4 class="font-semibold text-lg mb-4">Customer Rating</h4>
                    <div class="flex justify-center mb-4">
                        <div class="flex text-yellow-400 text-2xl">
                            ★★★★★
                        </div>
                    </div>
                    <p class="text-3xl font-bold text-yellow-600">4.9/5</p>
                    <p class="text-gray-500 text-sm">Based on 50,000+ reviews</p>
                </div>

                <!-- Packages Delivered -->
                <div class="bg-white rounded-xl p-6 text-center">
                    <h4 class="font-semibold text-lg mb-4">Packages Delivered</h4>
                    <div class="text-6xl mb-4">📦</div>
                    <p class="text-3xl font-bold text-blue-600">2.5M+</p>
                    <p class="text-gray-500 text-sm">This year alone</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section id="features" class="py-16 bg-white">
        <div class="max-w-6xl mx-auto px-6">
            <div class="text-center mb-12">
                <h3 class="font-montserrat text-3xl font-bold text-gray-900 mb-4">Why Choose Expresso Post?</h3>
                <p class="text-gray-600">Premium shipping services with unmatched reliability</p>
            </div>

            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div class="text-center p-6">
                    <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold text-lg mb-2">Lightning Fast</h4>
                    <p class="text-gray-600">Same-day and next-day delivery options available</p>
                </div>

                <div class="text-center p-6">
                    <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold text-lg mb-2">Secure & Safe</h4>
                    <p class="text-gray-600">Full insurance coverage and secure handling</p>
                </div>

                <div class="text-center p-6">
                    <div class="w-16 h-16 bg-purple-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold text-lg mb-2">Real-Time Tracking</h4>
                    <p class="text-gray-600">Track your package every step of the way</p>
                </div>

                <div class="text-center p-6">
                    <div class="w-16 h-16 bg-yellow-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-yellow-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold text-lg mb-2">Competitive Pricing</h4>
                    <p class="text-gray-600">Best rates in the industry with no hidden fees</p>
                </div>

                <div class="text-center p-6">
                    <div class="w-16 h-16 bg-red-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold text-lg mb-2">Eco-Friendly</h4>
                    <p class="text-gray-600">Carbon-neutral shipping options available</p>
                </div>

                <div class="text-center p-6">
                    <div class="w-16 h-16 bg-indigo-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-indigo-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18.364 5.636l-3.536 3.536m0 5.656l3.536 3.536M9.172 9.172L5.636 5.636m3.536 9.192L5.636 18.364M12 2.25a9.75 9.75 0 109.75 9.75A9.75 9.75 0 0012 2.25z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold text-lg mb-2">24/7 Support</h4>
                    <p class="text-gray-600">Round-the-clock customer service support</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-16 bg-gray-50">
        <div class="max-w-4xl mx-auto px-6">
            <div class="text-center mb-12">
                <h3 class="font-montserrat text-3xl font-bold text-gray-900 mb-4">Get In Touch</h3>
                <p class="text-gray-600">Ready to ship? Contact us for a quote or support</p>
            </div>

            <div class="grid md:grid-cols-3 gap-8 mb-12">
                <div class="text-center">
                    <div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-6 h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold mb-2">Address</h4>
                    <p class="text-gray-600 text-sm">123 Express Lane<br>Austin, TX 78701</p>
                </div>

                <div class="text-center">
                    <div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-6 h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold mb-2">Phone</h4>
                    <p class="text-gray-600 text-sm">1-800-EXPRESSO<br>(1-800-397-7377)</p>
                </div>

                <div class="text-center">
                    <div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-6 h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                        </svg>
                    </div>
                    <h4 class="font-semibold mb-2">Email</h4>
                    <p class="text-gray-600 text-sm">support@expressopost.com<br>quotes@expressopost.com</p>
                </div>
            </div>

            <!-- Contact Form -->
            <div class="bg-white rounded-xl p-8">
                <form onsubmit="handleContactForm(event)">
                    <div class="grid md:grid-cols-2 gap-6 mb-6">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-2">Name</label>
                            <input type="text" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                            <input type="email" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                        </div>
                    </div>
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-2">Subject</label>
                        <select class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                            <option>Get a Quote</option>
                            <option>Track a Package</option>
                            <option>Customer Support</option>
                            <option>Partnership Inquiry</option>
                        </select>
                    </div>
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-2">Message</label>
                        <textarea rows="4" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"></textarea>
                    </div>
                    <button type="submit" class="w-full px-8 py-3 bg-blue-900 text-white rounded-lg font-semibold hover:bg-blue-800 transition-colors">
                        Send Message
                    </button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-12">
        <div class="max-w-6xl mx-auto px-6">
            <div class="grid md:grid-cols-4 gap-8 mb-8">
                <div>
                    <div class="flex items-center gap-3 mb-4">
                        <div class="bg-white/10 p-2 rounded-md">
                            <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
                            </svg>
                        </div>
                        <span class="font-montserrat text-xl font-bold">Expresso Post</span>
                    </div>
                    <p class="text-gray-400 text-sm">Delivering confidence since 1995. Your trusted shipping partner.</p>
                </div>

                <div>
                    <h4 class="font-semibold mb-4">Services</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" class="hover:text-white">Same Day Delivery</a></li>
                        <li><a href="#" class="hover:text-white">Next Day Delivery</a></li>
                        <li><a href="#" class="hover:text-white">International Shipping</a></li>
                        <li><a href="#" class="hover:text-white">Freight Services</a></li>
                    </ul>
                </div>

                <div>
                    <h4 class="font-semibold mb-4">Support</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" class="hover:text-white">Track Package</a></li>
                        <li><a href="#" class="hover:text-white">Customer Service</a></li>
                        <li><a href="#" class="hover:text-white">Shipping Calculator</a></li>
                        <li><a href="#" class="hover:text-white">FAQ</a></li>
                    </ul>
                </div>

                <div>
                    <h4 class="font-semibold mb-4">Company</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" class="hover:text-white">About Us</a></li>
                        <li><a href="#" class="hover:text-white">Careers</a></li>
                        <li><a href="#" class="hover:text-white">Press</a></li>
                        <li><a href="#" class="hover:text-white">Investors</a></li>
                    </ul>
                </div>
            </div>

            <div class="border-t border-gray-800 pt-8 flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-400 text-sm">© 2024 Expresso Post. All rights reserved.</p>
                <div class="flex gap-6 text-sm text-gray-400 mt-4 md:mt-0">
                    <a href="#" class="hover:text-white">Privacy Policy</a>
                    <a href="#" class="hover:text-white">Terms of Service</a>
                    <a href="#" class="hover:text-white">Cookie Policy</a>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Mobile menu toggle
        function toggleMobileMenu() {
            const menu = document.getElementById('mobileMenu');
            menu.classList.toggle('hidden');
        }

        // Generate sample tracking ID
        function generateSampleTracking() {
            const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
            let sequence = "";
            for (let i = 0; i < 4; i++) {
                sequence += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            const trackingId = EXP-1995-TX-${sequence};
            document.getElementById('trackingInput').value = trackingId;
        }

        // Handle tracking form submission
        function handleTrack(event) {
            event.preventDefault();
            const input = document.getElementById('trackingInput').value.trim();
            
            if (!input) {
                alert('Please enter a tracking ID');
                return;
            }

            // Simulate tracking data
            const statuses = [
                { 
                    status: "In Transit", 
                    eta: "2 days", 
                    location: "Austin, TX",
                    color: "yellow",
                    icon: "🚛"
                },
                { 
                    status: "Out for Delivery", 
                    eta: "Today", 
                    location: "Austin Distribution Hub",
                    color: "blue",
                    icon: "🚚"
                },
                { 
                    status: "Delivered", 
                    eta: "—", 
                    location: "Recipient Address",
                    color: "green",
                    icon: "✅"
                }
            ];

            const randomStatus = statuses[Math.floor(Math.random() * statuses.length)];
            const carbonImpact = (Math.random() * 5).toFixed(2);
            const delayRisk = Math.random() < 0.12 ? "High" : "Low";
            const lastUpdated = new Date().toLocaleString();

            // Update UI
            document.getElementById('trackingId').textContent = input;
            document.getElementById('packageStatus').textContent = randomStatus.status;
            document.getElementById('packageEta').textContent = randomStatus.eta;
            document.getElementById('packageLocation').textContent = randomStatus.location;
            document.getElementById('carbonImpact').textContent = carbonImpact;
            document.getElementById('delayRisk').textContent = delayRisk;
            document.getElementById('lastUpdated').textContent = lastUpdated;

            // Update status icon color
            const statusIcon = document.getElementById('statusIcon');
            statusIcon.className = w-3 h-3 rounded-full bg-${randomStatus.color}-500;

            // Update delay risk color
            const delayRiskElement = document.getElementById('delayRisk');
            delayRiskElement.className = font-semibold ${delayRisk === 'High' ? 'text-red-600' : 'text-green-600'};

            // Show results
            document.getElementById('trackingResults').classList.remove('hidden');
        }

        // Handle contact form submission
        function handleContactForm(event) {
            event.preventDefault();
            alert('Thank you for your message! We\'ll get back to you within 24 hours.');
            event.target.reset();
        }

        // Show detailed tracking modal
        function showDetailedTracking() {
            const trackingId = document.getElementById('trackingInput').value.trim() || 'EXP-1995-TX-HN79';
            document.getElementById('detailedTrackingId').textContent = trackingId;
            document.getElementById('detailedTrackingModal').classList.remove('hidden');
            document.body.style.overflow = 'hidden'; // Prevent background scrolling
        }

        // Close detailed tracking modal
        function closeDetailedTracking() {
            document.getElementById('detailedTrackingModal').classList.add('hidden');
            document.body.style.overflow = 'auto'; // Restore scrolling
        }

        // Close modal when clicking outside
        document.getElementById('detailedTrackingModal').addEventListener('click', function(e) {
            if (e.target === this) {
                closeDetailedTracking();
            }
        });

        // Initialize chart when page loads
        window.addEventListener('load', function() {
            const ctx = document.getElementById('onTimeChart').getContext('2d');
            new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['On-time', 'Delayed'],
                    datasets: [{
                        data: [99.97, 0.03],
                        backgroundColor: ['#10B981', '#E5E7EB'],
                        borderWidth: 0,
                        cutout: '70%'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: true,
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return context.label + ': ' + context.parsed + '%';
                                }
                            }
                        }
                    }
                }
            });
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'96d009be61005ea2',t:'MTc1NDgzNDYyMS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
