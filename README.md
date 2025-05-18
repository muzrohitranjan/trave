<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toury - Explore the World</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: #e6f0fa;
            color: #333;
            line-height: 1.6;
        }

        /* Header */
        header {
            background: #1a3c6d;
            color: white;
            padding: 1rem 2rem;
            text-align: center;
        }

        header h1 {
            font-size: 1.5rem;
            font-weight: 600;
        }

        nav {
            margin-top: 1rem;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 1rem;
            font-size: 1rem;
            transition: color 0.3s ease;
        }

        nav a:hover {
            color: #f4a261;
        }

        /* Hero Section */
        .hero {
            background: url('https://via.placeholder.com/1200x500?text=Explore+the+World') center/cover no-repeat;
            height: 400px;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            position: relative;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
        }

        .hero h2 {
            font-size: 3rem;
            font-weight: 600;
            position: relative;
            z-index: 1;
        }

        /* Filter Section */
        .filter-section {
            padding: 2rem;
            background: #ffffff;
            text-align: center;
        }

        .filter-section label {
            font-weight: 600;
            margin-right: 0.5rem;
        }

        .filter-section select {
            padding: 0.5rem;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 1rem;
        }

        /* Gallery Section */
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
            padding: 2rem;
            background: #f9f9f9;
        }

        .destination {
            position: relative;
            cursor: pointer;
            border-radius: 8px;
            overflow: hidden;
            transition: transform 0.3s ease;
        }

        .destination img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            display: block;
        }

        .destination:hover {
            transform: scale(1.05);
        }

        .overlay {
            position: absolute;
            bottom: 0;
            background: rgba(0, 0, 0, 0.6);
            color: white;
            width: 100%;
            padding: 0.5rem;
            opacity: 0;
            transition: opacity 0.3s ease;
            text-align: center;
        }

        .destination:hover .overlay {
            opacity: 1;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .modal-content {
            background: white;
            padding: 2rem;
            border-radius: 8px;
            max-width: 500px;
            width: 90%;
            position: relative;
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        .close {
            position: absolute;
            top: 1rem;
            right: 1rem;
            cursor: pointer;
            font-size: 1.5rem;
            color: #333;
        }

        .close:focus {
            outline: 2px solid #f4a261;
        }

        /* Booking Form */
        .booking-section {
            padding: 2rem;
            background: #ffffff;
            max-width: 600px;
            margin: 0 auto;
        }

        .booking-section h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            text-align: center;
        }

        .booking-form {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            font-weight: 600;
            margin-bottom: 0.3rem;
        }

        .form-group input {
            padding: 0.5rem;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 1rem;
        }

        .form-group .error {
            color: #e63946;
            font-size: 0.9rem;
            margin-top: 0.3rem;
            display: none;
        }

        button {
            background: #1a3c6d;
            color: white;
            padding: 0.75rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            transition: background 0.3s ease;
        }

        button:hover {
            background: #f4a261;
        }

        /* Responsive Design */
        @media (max-width: 600px) {
            .gallery {
                grid-template-columns: 1fr;
            }

            .hero h2 {
                font-size: 2rem;
            }

            nav a {
                margin: 0 0.5rem;
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <h1>TOURY</h1>
        <nav>
            <a href="#home">Home</a>
            <a href="#about">About Us</a>
            <a href="#destinations">Destinations</a>
            <a href="#packages">Packages</a>
            <a href="#contact">Contact Us</a>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <h2>Journey to Explore World</h2>
    </section>

    <!-- Filter Section -->
    <section class="filter-section">
        <label for="regionFilter">Filter by Region:</label>
        <select id="regionFilter" onchange="filterDestinations()">
            <option value="all">All Regions</option>
            <option value="europe">Europe</option>
            <option value="asia">Asia</option>
            <option value="middle-east">Middle East</option>
        </select>
    </section>

    <!-- Destination Gallery -->
    <section class="gallery">
        <div class="destination" data-region="europe" data-name="Santorini" data-desc="Beautiful island in Greece with stunning views and white-washed buildings." onclick="openModal(this)">
            <img src="https://via.placeholder.com/300x200?text=Santorini" alt="Santorini">
            <div class="overlay">Santorini</div>
        </div>
        <div class="destination" data-region="asia" data-name="Kyoto Temple" data-desc="Experience the cultural beauty of Kyoto with its historic temples and gardens." onclick="openModal(this)">
            <img src="https://via.placeholder.com/300x200?text=Kyoto+Temple" alt="Kyoto Temple">
            <div class="overlay">Kyoto Temple</div>
        </div>
        <div class="destination" data-region="middle-east" data-name="Dubai Burj Khalifa" data-desc="Visit the tallest building in the world and enjoy the luxurious city of Dubai." onclick="openModal(this)">
            <img src="https://via.placeholder.com/300x200?text=Burj+Khalifa" alt="Burj Khalifa">
            <div class="overlay">Dubai Burj Khalifa</div>
        </div>
        <div class="destination" data-region="europe" data-name="Oxolotan River" data-desc="A relaxing river getaway in Europe, perfect for nature lovers." onclick="openModal(this)">
            <img src="https://via.placeholder.com/300x200?text=Oxolotan+River" alt="Oxolotan River">
            <div class="overlay">Oxolotan River</div>
        </div>
    </section>

    <!-- Modal -->
    <div id="modal" class="modal" role="dialog" aria-labelledby="modal-title" tabindex="-1">
        <div class="modal-content">
            <span class="close" onclick="closeModal()" role="button" aria-label="Close modal">&times;</span>
            <h2 id="modal-title"></h2>
            <p id="modal-desc"></p>
        </div>
    </div>

    <!-- Booking Form -->
    <section class="booking-section">
        <h3>Book Your Trip</h3>
        <form id="bookingForm" class="booking-form" onsubmit="return validateForm(event)">
            <div class="form-group">
                <label for="name">Full Name</label>
                <input type="text" id="name" placeholder="Full Name" required>
                <span class="error" id="nameError">Please enter your full name (min 3 characters).</span>
            </div>
            <div class="form-group">
                <label for="email">Email Address</label>
                <input type="email" id="email" placeholder="Email Address" required>
                <span class="error" id="emailError">Please enter a valid email address.</span>
            </div>
            <div class="form-group">
                <label for="travelDate">Travel Date</label>
                <input type="date" id="travelDate" required>
                <span class="error" id="dateError">Please select a future date.</span>
            </div>
            <div class="form-group">
                <label for="travelers">Number of Travelers</label>
                <input type="number" id="travelers" placeholder="Number of Travelers" min="1" required>
                <span class="error" id="travelersError">Please enter a valid number of travelers (at least 1).</span>
            </div>
            <button type="submit">Book Now</button>
        </form>
    </section>

    <script>
        // Modal Functions
        let currentTrigger = null;

        function openModal(element) {
            const modal = document.getElementById('modal');
            document.getElementById('modal-title').textContent = element.dataset.name;
            document.getElementById('modal-desc').textContent = element.dataset.desc;
            modal.style.display = 'flex';
            currentTrigger = element;
            modal.focus();

            // Trap focus in modal
            const focusableElements = modal.querySelectorAll('button, [tabindex]');
            const firstFocusable = focusableElements[0];
            const lastFocusable = focusableElements[focusableElements.length - 1];

            modal.addEventListener('keydown', (e) => {
                if (e.key === 'Tab') {
                    if (e.shiftKey && document.activeElement === firstFocusable) {
                        e.preventDefault();
                        lastFocusable.focus();
                    } else if (!e.shiftKey && document.activeElement === lastFocusable) {
                        e.preventDefault();
                        firstFocusable.focus();
                    }
                }
            });
        }

        function closeModal() {
            const modal = document.getElementById('modal');
            modal.style.display = 'none';
            if (currentTrigger) {
                currentTrigger.focus(); // Return focus to trigger element
            }
        }

        // Close modal on Esc key
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                closeModal();
            }
        });

        // Filter Destinations
        function filterDestinations() {
            const region = document.getElementById('regionFilter').value;
            const destinations = document.querySelectorAll('.destination');

            destinations.forEach(dest => {
                if (region === 'all' || dest.dataset.region === region) {
                    dest.style.display = '';
                } else {
                    dest.style.display = 'none';
                }
            });
        }

        // Form Validation
        function validateForm(event) {
            event.preventDefault();
            let isValid = true;

            // Reset error messages
            document.querySelectorAll('.error').forEach(error => error.style.display = 'none');

            // Name validation
            const name = document.getElementById('name').value.trim();
            if (name.length < 3) {
                document.getElementById('nameError').style.display = 'block';
                isValid = false;
            }

            // Email validation
            const email = document.getElementById('email').value.trim();
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailRegex.test(email)) {
                document.getElementById('emailError').style.display = 'block';
                isValid = false;
            }

            // Date validation
            const travelDate = new Date(document.getElementById('travelDate').value);
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            if (travelDate < today) {
                document.getElementById('dateError').style.display = 'block';
                isValid = false;
            }

            // Travelers validation
            const travelers = parseInt(document.getElementById('travelers').value);
            if (isNaN(travelers) || travelers < 1) {
                document.getElementById('travelersError').style.display = 'block';
                isValid = false;
            }

            if (isValid) {
                alert('Booking submitted successfully!');
                document.getElementById('bookingForm').reset();
            }

            return isValid;
        }
    </script>
</body>
</html>
