# Rooms---for---rent-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Rooms for Rent</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #f7f7f7;
    }

    header {
      background-color: #222;
      color: white;
      padding: 1rem;
      text-align: center;
      font-size: 1.8rem;
    }

    .container {
      max-width: 1100px;
      margin: 2rem auto;
      padding: 0 1rem;
    }

    .categories {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      justify-content: center;
      margin-bottom: 2rem;
    }

    .category-button {
      background-color: #444;
      color: white;
      padding: 0.75rem 1.5rem;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
      transition: 0.3s;
    }

    .category-button:hover, .category-button.active {
      background-color: #000;
    }

    .listings {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 1.5rem;
    }

    .card {
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      overflow: hidden;
      transition: 0.3s;
    }

    .card img {
      width: 100%;
      height: 160px;
      object-fit: cover;
    }

    .card-body {
      padding: 1rem;
    }

    .card-title {
      font-size: 1.2rem;
      font-weight: 600;
      margin-bottom: 0.5rem;
    }

    .card-location, .card-price {
      font-size: 0.95rem;
      margin-bottom: 0.3rem;
      color: #555;
    }

    .footer {
      margin-top: 4rem;
      text-align: center;
      font-size: 0.9rem;
      color: #888;
      padding-bottom: 2rem;
    }
  </style>
</head>
<body>
  <header>🏠 Rooms for Rent</header>

  <div class="container">
    <div class="categories">
      <button class="category-button active" onclick="filterListings('all')">All</button>
      <button class="category-button" onclick="filterListings('studio')">Studio Room</button>
      <button class="category-button" onclick="filterListings('flat')">Flat</button>
      <button class="category-button" onclick="filterListings('bed')">Bed Space</button>
      <button class="category-button" onclick="filterListings('shop')">Shop Space</button>
    </div>

    <div class="listings" id="listingContainer">
      <!-- Listings added by JS -->
    </div>
  </div>

  <div class="footer">&copy; 2025 RentHub | All rights reserved.</div>

  <script>
    const listings = [
      {
        title: 'Cozy Studio Room',
        price: 'AED 1,800/month',
        location: 'Dubai Marina',
        category: 'studio',
        img: 'https://source.unsplash.com/400x300/?studio,room'
      },
      {
        title: '2 BHK Flat',
        price: 'AED 4,500/month',
        location: 'Al Nahda, Sharjah',
        category: 'flat',
        img: 'https://source.unsplash.com/400x300/?apartment,interior'
      },
      {
        title: 'Bed Space for Gents',
        price: 'AED 700/month',
        location: 'Bur Dubai',
        category: 'bed',
        img: 'https://source.unsplash.com/400x300/?hostel,bed'
      },
      {
        title: 'Shop Space - 200 sq.ft',
        price: 'AED 5,000/month',
        location: 'Karama',
        category: 'shop',
        img: 'https://source.unsplash.com/400x300/?shop,storefront'
      },
      {
        title: 'Ladies Bed Space',
        price: 'AED 800/month',
        location: 'Al Qusais',
        category: 'bed',
        img: 'https://source.unsplash.com/400x300/?sharedroom,girls'
      },
      {
        title: 'Luxury Studio',
        price: 'AED 2,200/month',
        location: 'JLT',
        category: 'studio',
        img: 'https://source.unsplash.com/400x300/?modern,studio'
      },
    ];

    const listingContainer = document.getElementById("listingContainer");

    function displayListings(filter) {
      listingContainer.innerHTML = '';
      const filtered = filter === 'all' ? listings : listings.filter(item => item.category === filter);

      filtered.forEach(item => {
        listingContainer.innerHTML += `
          <div class="card">
            <img src="${item.img}" alt="${item.title}">
            <div class="card-body">
              <div class="card-title">${item.title}</div>
              <div class="card-price">${item.price}</div>
              <div class="card-location">${item.location}</div>
            </div>
          </div>
        `;
      });
    }

    function filterListings(category) {
      document.querySelectorAll(".category-button").forEach(btn => btn.classList.remove("active"));
      event.target.classList.add("active");
      displayListings(category);
    }

    // Show all listings on load
    displayListings('all');
  </script>
</body>
</html>
