<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Luxury Couture - Premium Shopify Theme</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <style>
        :root {
            --primary: #ff4e8d;
            --secondary: #3a0ca3;
            --dark: #14213d;
            --light: #f8f9fa;
            --accent: #f72585;
            --text: #333;
            --gray: #6c757d;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
        }

        body {
            background-color: #fff;
            color: var(--text);
            overflow-x: hidden;
        }

        /* Preloader */
        .preloader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--dark);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            animation: fadeOut 1s 3s forwards;
        }

        @keyframes fadeOut {
            to { opacity: 0; visibility: hidden; }
        }

        .logo-animation {
            font-size: 4rem;
            font-weight: 700;
            color: white;
            text-transform: uppercase;
            animation: zoomIn 1.5s ease-out, float 3s 1.5s infinite ease-in-out;
            text-shadow: 0 0 20px rgba(255,78,141,0.7);
        }

        @keyframes zoomIn {
            from { transform: scale(0.5); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        /* Header */
        header {
            background: white;
            box-shadow: 0 5px 30px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            z-index: 1000;
            padding: 15px 0;
            transition: all 0.3s ease;
        }

        .header-scrolled {
            padding: 10px 0;
            background: rgba(255,255,255,0.95);
            backdrop-filter: blur(10px);
        }

        .container {
            width: 90%;
            max-width: 1400px;
            margin: 0 auto;
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--dark);
            text-decoration: none;
            display: flex;
            align-items: center;
        }

        .logo i {
            color: var(--primary);
            margin-right: 10px;
            font-size: 1.5rem;
        }

        /* Navigation */
        .main-nav ul {
            display: flex;
            list-style: none;
        }

        .main-nav ul li {
            margin: 0 15px;
            position: relative;
        }

        .main-nav ul li a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
        }

        .main-nav ul li a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s ease;
        }

        .main-nav ul li a:hover::after {
            width: 100%;
        }

        .main-nav ul li a:hover {
            color: var(--primary);
        }

        .header-actions {
            display: flex;
            align-items: center;
        }

        .search-box {
            position: relative;
            margin-right: 20px;
        }

        .search-input {
            width: 0;
            padding: 0;
            border: none;
            border-bottom: 2px solid transparent;
            background: transparent;
            transition: all 0.3s ease;
            position: absolute;
            right: 30px;
            top: 50%;
            transform: translateY(-50%);
        }

        .search-input.active {
            width: 200px;
            padding: 5px 10px;
            border-color: var(--primary);
        }

        .search-btn {
            background: none;
            border: none;
            color: var(--dark);
            font-size: 1.2rem;
            cursor: pointer;
            transition: color 0.3s ease;
        }

        .search-btn:hover {
            color: var(--primary);
        }

        .cart-btn, .profile-btn {
            position: relative;
            background: none;
            border: none;
            color: var(--dark);
            font-size: 1.2rem;
            cursor: pointer;
            transition: color 0.3s ease;
            margin-left: 15px;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: var(--primary);
            color: white;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
            font-weight: bold;
        }

        .cart-btn:hover, .profile-btn:hover {
            color: var(--primary);
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--dark);
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Profile Dropdown */
        .profile-dropdown {
            position: absolute;
            top: 50px;
            right: 0;
            background: white;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            border-radius: 10px;
            padding: 20px;
            width: 250px;
            z-index: 100;
            opacity: 0;
            visibility: hidden;
            transform: translateY(20px);
            transition: all 0.3s ease;
        }

        .profile-dropdown.active {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        .profile-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }

        .profile-img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            margin-right: 15px;
        }

        .profile-name {
            font-weight: 600;
        }

        .profile-email {
            font-size: 0.8rem;
            color: var(--gray);
        }

        .profile-links {
            list-style: none;
        }

        .profile-links li {
            margin-bottom: 10px;
        }

        .profile-links a {
            color: var(--dark);
            text-decoration: none;
            display: flex;
            align-items: center;
            transition: all 0.3s ease;
        }

        .profile-links a:hover {
            color: var(--primary);
            padding-left: 5px;
        }

        .profile-links i {
            margin-right: 10px;
            width: 20px;
            text-align: center;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
            padding-top: 80px;
        }

        .hero-slider {
            width: 100%;
            height: 100%;
            position: relative;
        }

        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            opacity: 0;
            transition: opacity 1s ease-in-out, transform 1s ease-in-out;
            display: flex;
            align-items: center;
        }

        .slide.active {
            opacity: 1;
            transform: scale(1);
        }

        .slide.next {
            transform: scale(1.05);
        }

        .slide::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.3);
        }

        .slide-1 {
            background-image: url('https://images.unsplash.com/photo-1483985988355-763728e1935b?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80');
        }

        .slide-2 {
            background-image: url('https://images.unsplash.com/photo-1525507119028-ed4c629a60a3?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80');
        }

        .slide-3 {
            background-image: url('https://images.unsplash.com/photo-1542060748-10c28b62716f?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80');
        }

        .hero-content {
            position: relative;
            z-index: 1;
            color: white;
            max-width: 600px;
            padding: 0 50px;
            transform: translateY(50px);
            opacity: 0;
            transition: all 1s ease;
        }

        .slide.active .hero-content {
            transform: translateY(0);
            opacity: 1;
        }

        .hero-subtitle {
            font-size: 1.2rem;
            margin-bottom: 15px;
            display: inline-block;
            animation: fadeInLeft 1s ease-out;
        }

        .hero-title {
            font-size: 3.5rem;
            font-weight: 700;
            margin-bottom: 20px;
            line-height: 1.2;
            animation: fadeInLeft 1s 0.3s ease-out both;
        }

        .hero-text {
            font-size: 1.1rem;
            margin-bottom: 30px;
            animation: fadeInLeft 1s 0.6s ease-out both;
        }

        .hero-btn {
            display: inline-block;
            background: var(--primary);
            color: white;
            padding: 15px 40px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            animation: fadeInUp 1s 0.9s ease-out both;
            box-shadow: 0 10px 20px rgba(247,37,133,0.3);
        }

        .hero-btn:hover {
            background: #ff2d7a;
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(247,37,133,0.4);
        }

        .slider-controls {
            position: absolute;
            bottom: 50px;
            left: 50px;
            z-index: 2;
            display: flex;
        }

        .slider-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255,255,255,0.5);
            margin-right: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .slider-dot.active {
            background: white;
            transform: scale(1.3);
        }

        /* Featured Categories */
        .featured-categories {
            padding: 100px 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
            position: relative;
        }

        .section-title h2 {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--dark);
            display: inline-block;
            position: relative;
            padding-bottom: 15px;
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 3px;
            background: var(--primary);
        }

        .categories-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .category-card {
            position: relative;
            height: 400px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: all 0.5s ease;
        }

        .category-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.2);
        }

        .category-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .category-card:hover .category-image {
            transform: scale(1.05);
        }

        .category-content {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 30px;
            background: linear-gradient(to top, rgba(0,0,0,0.8), transparent);
            color: white;
            transform: translateY(20px);
            opacity: 0;
            transition: all 0.5s ease;
        }

        .category-card:hover .category-content {
            transform: translateY(0);
            opacity: 1;
        }

        .category-title {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .category-link {
            display: inline-block;
            color: white;
            text-decoration: none;
            font-weight: 600;
            margin-top: 15px;
            position: relative;
        }

        .category-link::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s ease;
        }

        .category-link:hover::after {
            width: 100%;
        }

        /* Featured Products */
        .featured-products {
            padding: 100px 0;
            background: var(--light);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 30px;
        }

        .product-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            transition: all 0.3s ease;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);
        }

        .product-badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--primary);
            color: white;
            padding: 5px 15px;
            border-radius: 30px;
            font-size: 0.8rem;
            font-weight: 600;
            z-index: 1;
        }

        .product-image-container {
            position: relative;
            height: 300px;
            overflow: hidden;
        }

        .product-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .product-card:hover .product-image {
            transform: scale(1.1);
        }

        .product-actions {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            display: flex;
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }

        .product-card:hover .product-actions {
            transform: translateY(0);
        }

        .action-btn {
            flex: 1;
            padding: 15px;
            border: none;
            background: rgba(255,255,255,0.9);
            color: var(--dark);
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .action-btn i {
            margin-right: 8px;
        }

        .action-btn:hover {
            background: white;
            color: var(--primary);
        }

        .add-to-cart {
            background: var(--dark);
            color: white;
        }

        .add-to-cart:hover {
            background: var(--primary);
            color: white;
        }

        .product-info {
            padding: 20px;
        }

        .product-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 10px;
            color: var(--dark);
        }

        .product-price {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .current-price {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--primary);
        }

        .old-price {
            font-size: 0.9rem;
            text-decoration: line-through;
            color: var(--gray);
            margin-left: 10px;
        }

        .product-rating {
            color: #ffc107;
            margin-bottom: 15px;
        }

        .product-colors {
            display: flex;
            gap: 8px;
        }

        .color-option {
            width: 20px;
            height: 20px;
            border-radius: 50%;
            cursor: pointer;
            border: 1px solid #eee;
            transition: transform 0.3s ease;
        }

        .color-option:hover {
            transform: scale(1.2);
        }

        /* About Section */
        .about-section {
            padding: 100px 0;
            background: url('https://images.unsplash.com/photo-1521747116042-5a810fda9664?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80') center/cover no-repeat fixed;
            position: relative;
            color: white;
        }

        .about-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(20,33,61,0.8);
        }

        .about-content {
            position: relative;
            z-index: 1;
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }

        .about-title {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 30px;
        }

        .about-text {
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 40px;
        }

        .about-text p {
            margin-bottom: 20px;
        }

        .about-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 30px;
            margin-top: 50px;
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 10px;
        }

        .stat-label {
            font-size: 1.1rem;
            font-weight: 600;
        }

        /* Newsletter */
        .newsletter-section {
            padding: 80px 0;
            background: var(--primary);
            color: white;
            text-align: center;
        }

        .newsletter-container {
            max-width: 600px;
            margin: 0 auto;
        }

        .newsletter-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 20px;
        }

        .newsletter-text {
            font-size: 1.1rem;
            margin-bottom: 30px;
        }

        .newsletter-form {
            display: flex;
            max-width: 500px;
            margin: 0 auto;
        }

        .newsletter-input {
            flex: 1;
            padding: 15px 20px;
            border: none;
            border-radius: 30px 0 0 30px;
            font-size: 1rem;
            outline: none;
        }

        .newsletter-btn {
            padding: 15px 30px;
            background: var(--dark);
            color: white;
            border: none;
            border-radius: 0 30px 30px 0;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .newsletter-btn:hover {
            background: #0d1b3a;
        }

        /* Footer */
        .footer {
            background: var(--dark);
            color: white;
            padding: 80px 0 30px;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 50px;
        }

        .footer-logo {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 20px;
            display: inline-block;
        }

        .footer-about {
            margin-bottom: 20px;
            line-height: 1.8;
        }

        .footer-social {
            display: flex;
            gap: 15px;
        }

        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255,255,255,0.1);
            color: white;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            background: var(--primary);
            transform: translateY(-5px);
        }

        .footer-title {
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }

        .footer-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 40px;
            height: 2px;
            background: var(--primary);
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 10px;
        }

        .footer-links a {
            color: #bbb;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .footer-links a:hover {
            color: white;
            padding-left: 5px;
        }

        .footer-contact p {
            margin-bottom: 15px;
            display: flex;
            align-items: center;
        }

        .footer-contact i {
            margin-right: 10px;
            color: var(--primary);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        /* Search Results */
        .search-results {
            position: absolute;
            top: 50px;
            right: 0;
            width: 300px;
            background: white;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            border-radius: 10px;
            padding: 20px;
            z-index: 100;
            opacity: 0;
            visibility: hidden;
            transform: translateY(20px);
            transition: all 0.3s ease;
        }

        .search-results.active {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        .search-result-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .search-result-item {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #f5f5f5;
        }

        .search-result-img {
            width: 60px;
            height: 60px;
            object-fit: cover;
            border-radius: 5px;
            margin-right: 15px;
        }

        .search-result-info h4 {
            font-size: 0.9rem;
            margin-bottom: 5px;
        }

        .search-result-price {
            font-weight: 700;
            color: var(--primary);
        }

        .view-all-results {
            display: block;
            text-align: center;
            color: var(--primary);
            font-weight: 600;
            margin-top: 10px;
        }

        /* Responsive */
        @media (max-width: 992px) {
            .hero-title {
                font-size: 3rem;
            }
        }

        @media (max-width: 768px) {
            .mobile-menu-btn {
                display: block;
            }

            .main-nav {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 80%;
                height: calc(100vh - 80px);
                background: white;
                box-shadow: 0 10px 30px rgba(0,0,0,0.1);
                transition: all 0.5s ease;
                padding: 30px;
            }

            .main-nav.active {
                left: 0;
            }

            .main-nav ul {
                flex-direction: column;
            }

            .main-nav ul li {
                margin: 15px 0;
            }

            .hero-title {
                font-size: 2.5rem;
            }

            .hero-content {
                padding: 0 20px;
            }

            .slider-controls {
                left: 20px;
                bottom: 20px;
            }

            .profile-dropdown {
                right: 20px;
            }

            .search-results {
                right: 20px;
                width: calc(100% - 40px);
            }
        }

        @media (max-width: 576px) {
            .hero-title {
                font-size: 2rem;
            }

            .hero-btn {
                padding: 12px 30px;
            }

            .newsletter-form {
                flex-direction: column;
            }

            .newsletter-input {
                border-radius: 30px;
                margin-bottom: 10px;
            }

            .newsletter-btn {
                border-radius: 30px;
            }
        }

        /* Animations */
        .animate-on-scroll {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .animate-on-scroll.animated {
            opacity: 1;
            transform: translateY(0);
        }

        @keyframes fadeInLeft {
            from { opacity: 0; transform: translateX(-50px); }
            to { opacity: 1; transform: translateX(0); }
        }

        @keyframes fadeInRight {
            from { opacity: 0; transform: translateX(50px); }
            to { opacity: 1; transform: translateX(0); }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(50px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        /* Page transitions */
        .page-transition {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--primary);
            z-index: 9998;
            transform: scaleY(0);
            transform-origin: bottom;
            transition: transform 0.6s ease-in-out;
        }

        .page-transition.active {
            transform: scaleY(1);
            transform-origin: top;
        }
    </style>
</head>
<body>
    <!-- Preloader -->
    <div class="preloader">
        <div class="logo-animation">Luxury Couture</div>
    </div>

    <!-- Page Transition -->
    <div class="page-transition"></div>

    <!-- Header -->
    <header id="header">
        <div class="container">
            <div class="header-container">
                <a href="#home" class="logo animate-on-scroll"><i class="fas fa-crown"></i> Luxury Couture</a>
                
                <nav class="main-nav">
                    <ul>
                        <li><a href="#home" class="active">Home</a></li>
                        <li><a href="#shop">Shop</a></li>
                        <li><a href="#collections">Collections</a></li>
                        <li><a href="#about">About</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </nav>
                
                <div class="header-actions animate-on-scroll">
                    <div class="search-box">
                        <input type="text" class="search-input" placeholder="Search products...">
                        <button class="search-btn"><i class="fas fa-search"></i></button>
                        <div class="search-results">
                            <h4 class="search-result-title">Search Results</h4>
                            <div class="search-result-item">
                                <img src="https://images.unsplash.com/photo-1529374255404-311a2a4f1fd9?ixlib=rb-1.2.1&auto=format&fit=crop&w=200&q=80" alt="Product" class="search-result-img">
                                <div class="search-result-info">
                                    <h4>Denim Jacket</h4>
                                    <div class="search-result-price">$89.99</div>
                                </div>
                            </div>
                            <div class="search-result-item">
                                <img src="https://images.unsplash.com/photo-1542060748-10c28b62716f?ixlib=rb-1.2.1&auto=format&fit=crop&w=200&q=80" alt="Product" class="search-result-img">
                                <div class="search-result-info">
                                    <h4>Floral Summer Dress</h4>
                                    <div class="search-result-price">$59.99</div>
                                </div>
                            </div>
                            <a href="#" class="view-all-results">View all results</a>
                        </div>
                    </div>
                    <button class="cart-btn">
                        <i class="fas fa-shopping-bag"></i>
                        <span class="cart-count">0</span>
                    </button>
                    <div class="profile-btn-container">
                        <button class="profile-btn">
                            <i class="fas fa-user"></i>
                        </button>
                        <div class="profile-dropdown">
                            <div class="profile-header">
                                <div class="profile-img">JD</div>
                                <div>
                                    <div class="profile-name">John Doe</div>
                                    <div class="profile-email">john@example.com</div>
                                </div>
                            </div>
                            <ul class="profile-links">
                                <li><a href="#"><i class="fas fa-user"></i> My Profile</a></li>
                                <li><a href="#"><i class="fas fa-shopping-bag"></i> My Orders</a></li>
                                <li><a href="#"><i class="fas fa-heart"></i> Wishlist</a></li>
                                <li><a href="#"><i class="fas fa-cog"></i> Settings</a></li>
                                <li><a href="#"><i class="fas fa-sign-out-alt"></i> Logout</a></li>
                            </ul>
                        </div>
                    </div>
                    <button class="mobile-menu-btn">
                        <i class="fas fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-slider">
            <!-- Slide 1 -->
            <div class="slide slide-1 active">
                <div class="hero-content">
                    <span class="hero-subtitle">New Collection</span>
                    <h1 class="hero-title">Summer Fashion 2023</h1>
                    <p class="hero-text">Discover our exclusive collection of summer outfits designed for comfort and style.</p>
                    <a href="#shop" class="hero-btn">Shop Now</a>
                </div>
            </div>
            
            <!-- Slide 2 -->
            <div class="slide slide-2">
                <div class="hero-content">
                    <span class="hero-subtitle">Limited Offer</span>
                    <h1 class="hero-title">Up to 50% Off</h1>
                    <p class="hero-text">Don't miss our seasonal sale with huge discounts on selected items.</p>
                    <a href="#collections" class="hero-btn">View Offers</a>
                </div>
            </div>
            
            <!-- Slide 3 -->
            <div class="slide slide-3">
                <div class="hero-content">
                    <span class="hero-subtitle">Premium Quality</span>
                    <h1 class="hero-title">Luxury Accessories</h1>
                    <p class="hero-text">Elevate your style with our handcrafted accessories collection.</p>
                    <a href="#collections" class="hero-btn">Explore</a>
                </div>
            </div>
        </div>
        
        <div class="slider-controls">
            <div class="slider-dot active" data-slide="0"></div>
            <div class="slider-dot" data-slide="1"></div>
            <div class="slider-dot" data-slide="2"></div>
        </div>
    </section>

    <!-- Featured Categories -->
    <section class="featured-categories" id="collections">
        <div class="container">
            <div class="section-title animate-on-scroll">
                <h2>Our Collections</h2>
            </div>
            
            <div class="categories-grid">
                <!-- Category 1 -->
                <div class="category-card animate-on-scroll">
                    <img src="https://images.unsplash.com/photo-1551232864-3f0890e580d9?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Men's Fashion" class="category-image">
                    <div class="category-content">
                        <h3 class="category-title">Men's Fashion</h3>
                        <a href="#shop" class="category-link">Shop Now <i class="fas fa-arrow-right"></i></a>
                    </div>
                </div>
                
                <!-- Category 2 -->
                <div class="category-card animate-on-scroll">
                    <img src="https://images.unsplash.com/photo-1525507119028-ed4c629a60a3?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Women's Fashion" class="category-image">
                    <div class="category-content">
                        <h3 class="category-title">Women's Fashion</h3>
                        <a href="#shop" class="category-link">Shop Now <i class="fas fa-arrow-right"></i></a>
                    </div>
                </div>
                
                <!-- Category 3 -->
                <div class="category-card animate-on-scroll">
                    <img src="https://images.unsplash.com/photo-1595950653106-6c9ebd614d3a?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Accessories" class="category-image">
                    <div class="category-content">
                        <h3 class="category-title">Accessories</h3>
                        <a href="#shop" class="category-link">Shop Now <i class="fas fa-arrow-right"></i></a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Featured Products -->
    <section class="featured-products" id="shop">
        <div class="container">
            <div class="section-title animate-on-scroll">
                <h2>Featured Products</h2>
            </div>
            
            <div class="products-grid">
                <!-- Product 1 -->
                <div class="product-card animate-on-scroll">
                    <span class="product-badge">New</span>
                    <div class="product-image-container">
                        <img src="https://images.unsplash.com/photo-1529374255404-311a2a4f1fd9?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Denim Jacket" class="product-image">
                        <div class="product-actions">
                            <button class="action-btn"><i class="far fa-heart"></i> Wishlist</button>
                            <button class="action-btn add-to-cart"><i class="fas fa-shopping-cart"></i> Add to Cart</button>
                        </div>
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Premium Denim Jacket</h3>
                        <div class="product-price">
                            <span class="current-price">$89.99</span>
                            <span class="old-price">$120.00</span>
                        </div>
                        <div class="product-rating">
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star-half-alt"></i>
                        </div>
                        <div class="product-colors">
                            <div class="color-option" style="background-color: #000;"></div>
                            <div class="color-option" style="background-color: #1e40af;"></div>
                            <div class="color-option" style="background-color: #444;"></div>
                        </div>
                    </div>
                </div>
                
                <!-- Product 2 -->
                <div class="product-card animate-on-scroll">
                    <div class="product-image-container">
                        <img src="https://images.unsplash.com/photo-1542060748-10c28b62716f?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Summer Dress" class="product-image">
                        <div class="product-actions">
                            <button class="action-btn"><i class="far fa-heart"></i> Wishlist</button>
                            <button class="action-btn add-to-cart"><i class="fas fa-shopping-cart"></i> Add to Cart</button>
                        </div>
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Floral Summer Dress</h3>
                        <div class="product-price">
                            <span class="current-price">$59.99</span>
                        </div>
                        <div class="product-rating">
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="far fa-star"></i>
                        </div>
                        <div class="product-colors">
                            <div class="color-option" style="background-color: #f43f5e;"></div>
                            <div class="color-option" style="background-color: #f59e0b;"></div>
                            <div class="color-option" style="background-color: #10b981;"></div>
                        </div>
                    </div>
                </div>
                
                <!-- Product 3 -->
                <div class="product-card animate-on-scroll">
                    <span class="product-badge">Sale</span>
                    <div class="product-image-container">
                        <img src="https://images.unsplash.com/photo-1591047139829-d91aecb6caea?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Casual Shirt" class="product-image">
                        <div class="product-actions">
                            <button class="action-btn"><i class="far fa-heart"></i> Wishlist</button>
                            <button class="action-btn add-to-cart"><i class="fas fa-shopping-cart"></i> Add to Cart</button>
                        </div>
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Casual Linen Shirt</h3>
                        <div class="product-price">
                            <span class="current-price">$39.99</span>
                            <span class="old-price">$49.99</span>
                        </div>
                        <div class="product-rating">
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                        </div>
                        <div class="product-colors">
                            <div class="color-option" style="background-color: #3b82f6;"></div>
                            <div class="color-option" style="background-color: #fff; border: 1px solid #ddd;"></div>
                            <div class="color-option" style="background-color: #10b981;"></div>
                        </div>
                    </div>
                </div>
                
                <!-- Product 4 -->
                <div class="product-card animate-on-scroll">
                    <div class="product-image-container">
                        <img src="https://images.unsplash.com/photo-1527719327859-c6ce80353573?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Sports Shoes" class="product-image">
                        <div class="product-actions">
                            <button class="action-btn"><i class="far fa-heart"></i> Wishlist</button>
                            <button class="action-btn add-to-cart"><i class="fas fa-shopping-cart"></i> Add to Cart</button>
                        </div>
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">Running Sports Shoes</h3>
                        <div class="product-price">
                            <span class="current-price">$129.99</span>
                        </div>
                        <div class="product-rating">
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star-half-alt"></i>
                        </div>
                        <div class="product-colors">
                            <div class="color-option" style="background-color: #000;"></div>
                            <div class="color-option" style="background-color: #3b82f6;"></div>
                            <div class="color-option" style="background-color: #ef4444;"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="about-section" id="about">
        <div class="container">
            <div class="about-content animate-on-scroll">
                <h2 class="about-title">Our Story</h2>
                <div class="about-text">
                    <p>
                        Founded in 2010, Luxury Couture has grown from a small boutique to a leading fashion destination. 
                        We're committed to providing high-quality, stylish clothing that makes you look and feel your best. 
                        Our team of designers works tirelessly to create unique pieces that combine comfort with cutting-edge style.
                    </p>
                    <p>
                        Sustainability is at the heart of what we do. We partner with ethical manufacturers and use eco-friendly 
                        materials to reduce our environmental impact while delivering exceptional fashion.
                    </p>
                    <p>
                        Our mission is to empower individuals to express their unique style through carefully curated collections 
                        that blend timeless elegance with contemporary trends.
                    </p>
                </div>
                
                <div class="about-stats">
                    <div class="stat-item animate-on-scroll">
                        <div class="stat-number">12+</div>
                        <div class="stat-label">Years Experience</div>
                    </div>
                    <div class="stat-item animate-on-scroll">
                        <div class="stat-number">500+</div>
                        <div class="stat-label">Happy Clients</div>
                    </div>
                    <div class="stat-item animate-on-scroll">
                        <div class="stat-number">50+</div>
                        <div class="stat-label">Fashion Awards</div>
                    </div>
                    <div class="stat-item animate-on-scroll">
                        <div class="stat-number">100%</div>
                        <div class="stat-label">Satisfaction</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Newsletter -->
    <section class="newsletter-section">
        <div class="container">
            <div class="newsletter-container animate-on-scroll">
                <h2 class="newsletter-title">Join Our Newsletter</h2>
                <p class="newsletter-text">Subscribe to get 15% off your first order and be the first to know about new arrivals and exclusive offers.</p>
                <form class="newsletter-form">
                    <input type="email" class="newsletter-input" placeholder="Your email address" required>
                    <button type="submit" class="newsletter-btn">Subscribe</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer" id="contact">
        <div class="container">
            <div class="footer-grid">
                <div class="footer-col animate-on-scroll">
                    <a href="#" class="footer-logo"><i class="fas fa-crown"></i> Luxury Couture</a>
                    <p class="footer-about">
                        Premium fashion destination offering the latest trends in clothing, accessories and footwear for men and women.
                    </p>
                    <div class="footer-social">
                        <a href="#" class="social-link"><i class="fab fa-facebook-f"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-pinterest-p"></i></a>
                    </div>
                </div>
                
                <div class="footer-col animate-on-scroll">
                    <h3 class="footer-title">Quick Links</h3>
                    <ul class="footer-links">
                        <li><a href="#home">Home</a></li>
                        <li><a href="#shop">Shop</a></li>
                        <li><a href="#collections">Collections</a></li>
                        <li><a href="#about">About Us</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </div>
                
                <div class="footer-col animate-on-scroll">
                    <h3 class="footer-title">Customer Service</h3>
                    <ul class="footer-links">
                        <li><a href="#">Shipping Policy</a></li>
                        <li><a href="#">Return Policy</a></li>
                        <li><a href="#">Privacy Policy</a></li>
                        <li><a href="#">Terms & Conditions</a></li>
                        <li><a href="#">FAQs</a></li>
                    </ul>
                </div>
                
                <div class="footer-col animate-on-scroll">
                    <h3 class="footer-title">Contact Us</h3>
                    <div class="footer-contact">
                        <p><i class="fas fa-map-marker-alt"></i> 123 Fashion Street, New York, NY 10001</p>
                        <p><i class="fas fa-phone"></i> +1 (555) 123-4567</p>
                        <p><i class="fas fa-envelope"></i> info@luxurycouture.com</p>
                        <p><i class="fas fa-clock"></i> Mon-Fri: 9AM - 6PM</p>
                    </div>
                </div>
            </div>
            
            <div class="footer-bottom animate-on-scroll">
                <p>&copy; 2023 Luxury Couture. All Rights Reserved. Designed for ThemeForest</p>
            </div>
        </div>
    </footer>

    <script>
        // Preloader
        window.addEventListener('load', function() {
            setTimeout(function() {
                document.querySelector('.preloader').style.opacity = '0';
                setTimeout(function() {
                    document.querySelector('.preloader').style.display = 'none';
                }, 1000);
            }, 2000);
        });

        // Header scroll effect
        window.addEventListener('scroll', function() {
            const header = document.getElementById('header');
            if (window.scrollY > 100) {
                header.classList.add('header-scrolled');
            } else {
                header.classList.remove('header-scrolled');
            }
        });

        // Mobile menu toggle
        const mobileMenuBtn = document.querySelector('.mobile-menu-btn');
        const mainNav = document.querySelector('.main-nav');

        mobileMenuBtn.addEventListener('click', function() {
            mainNav.classList.toggle('active');
            this.innerHTML = mainNav.classList.contains('active') ? 
                '<i class="fas fa-times"></i>' : '<i class="fas fa-bars"></i>';
        });

        // Close mobile menu when clicking on a link
        const navLinks = document.querySelectorAll('.main-nav a');
        navLinks.forEach(link => {
            link.addEventListener('click', function() {
                mainNav.classList.remove('active');
                mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
            });
        });

        // Search toggle
        const searchBtn = document.querySelector('.search-btn');
        const searchInput = document.querySelector('.search-input');
        const searchResults = document.querySelector('.search-results');

        searchBtn.addEventListener('click', function(e) {
            e.preventDefault();
            searchInput.classList.toggle('active');
            if (searchInput.classList.contains('active')) {
                searchInput.focus();
            } else {
                searchResults.classList.remove('active');
            }
        });

        // Show search results when typing
        searchInput.addEventListener('input', function() {
            if (this.value.length > 0) {
                searchResults.classList.add('active');
            } else {
                searchResults.classList.remove('active');
            }
        });

        // Profile dropdown
        const profileBtn = document.querySelector('.profile-btn');
        const profileDropdown = document.querySelector('.profile-dropdown');

        profileBtn.addEventListener('click', function(e) {
            e.stopPropagation();
            profileDropdown.classList.toggle('active');
        });

        // Close dropdown when clicking outside
        document.addEventListener('click', function() {
            profileDropdown.classList.remove('active');
        });

        // Hero slider
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const dots = document.querySelectorAll('.slider-dot');

        function showSlide(n) {
            // Set current slide to "next" state before changing
            slides[currentSlide].classList.add('next');
            
            setTimeout(() => {
                slides.forEach(slide => {
                    slide.classList.remove('active');
                    slide.classList.remove('next');
                });
                dots.forEach(dot => dot.classList.remove('active'));
                
                currentSlide = (n + slides.length) % slides.length;
                slides[currentSlide].classList.add('active');
                dots[currentSlide].classList.add('active');
            }, 500);
        }

        dots.forEach((dot, index) => {
            dot.addEventListener('click', () => showSlide(index));
        });

        // Auto slide change
        setInterval(() => {
            showSlide(currentSlide + 1);
        }, 5000);

        // Add to cart functionality
        const addToCartButtons = document.querySelectorAll('.add-to-cart');
        const cartCount = document.querySelector('.cart-count');
        let count = 0;

        addToCartButtons.forEach(button => {
            button.addEventListener('click', function(e) {
                e.preventDefault();
                count++;
                cartCount.textContent = count;
                
                // Animation
                const productCard = this.closest('.product-card');
                const productImage = productCard.querySelector('.product-image');
                const rect = productImage.getBoundingClientRect();
                
                const flyingItem = document.createElement('div');
                flyingItem.style.position = 'fixed';
                flyingItem.style.width = '50px';
                flyingItem.style.height = '50px';
                flyingItem.style.backgroundImage = `url(${productImage.src})`;
                flyingItem.style.backgroundSize = 'cover';
                flyingItem.style.borderRadius = '50%';
                flyingItem.style.zIndex = '9999';
                flyingItem.style.left = `${rect.left}px`;
                flyingItem.style.top = `${rect.top}px`;
                flyingItem.style.transition = 'all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55)';
                document.body.appendChild(flyingItem);
                
                setTimeout(() => {
                    const cartRect = document.querySelector('.cart-btn').getBoundingClientRect();
                    flyingItem.style.left = `${cartRect.left}px`;
                    flyingItem.style.top = `${cartRect.top}px`;
                    flyingItem.style.width = '10px';
                    flyingItem.style.height = '10px';
                    flyingItem.style.opacity = '0.5';
                }, 10);
                
                setTimeout(() => {
                    flyingItem.remove();
                    cartCount.style.transform = 'scale(1.5)';
                    setTimeout(() => {
                        cartCount.style.transform = 'scale(1)';
                    }, 200);
                }, 800);
            });
        });

        // Page transition for navigation
        const pageTransition = document.querySelector('.page-transition');
        const internalLinks = document.querySelectorAll('a[href^="#"]');

        internalLinks.forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                if (targetElement) {
                    // Start page transition
                    pageTransition.classList.add('active');
                    
                    setTimeout(() => {
                        window.scrollTo({
                            top: targetElement.offsetTop - 80,
                            behavior: 'smooth'
                        });
                        
                        // Update active nav link
                        document.querySelectorAll('.main-nav a').forEach(navLink => {
                            navLink.classList.remove('active');
                        });
                        this.classList.add('active');
                        
                        // End page transition
                        setTimeout(() => {
                            pageTransition.classList.remove('active');
                        }, 600);
                    }, 600);
                }
            });
        });

        // Animation on scroll
        function animateOnScroll() {
            const elements = document.querySelectorAll('.animate-on-scroll');
            
            elements.forEach(element => {
                const elementPosition = element.getBoundingClientRect().top;
                const screenPosition = window.innerHeight / 1.2;
                
                if (elementPosition < screenPosition) {
                    element.classList.add('animated');
                }
            });
        }

        window.addEventListener('scroll', animateOnScroll);
        animateOnScroll(); // Run once on page load

        // Newsletter form submission
        const newsletterForm = document.querySelector('.newsletter-form');
        if (newsletterForm) {
            newsletterForm.addEventListener('submit', function(e) {
                e.preventDefault();
                const email = this.querySelector('input').value;
                alert(`Thank you for subscribing with ${email}! You'll receive 15% off your first order.`);
                this.reset();
            });
        }

        // Page load animation
        document.body.style.opacity = '0';
        setTimeout(() => {
            document.body.style.transition = 'opacity 1s ease';
            document.body.style.opacity = '1';
        }, 100);
    </script>
</body>
</html>
