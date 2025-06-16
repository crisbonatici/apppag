{
  "name": "vite-react-typescript-starter",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "lucide-react": "^0.344.0",
    "react": "^18.3.1",
    "react-dom": "^18.3.1"
  },
  "devDependencies": {
    "@eslint/js": "^9.9.1",
    "@types/react": "^18.3.5",
    "@types/react-dom": "^18.3.0",
    "@vitejs/plugin-react": "^4.3.1",
    "autoprefixer": "^10.4.18",
    "eslint": "^9.9.1",
    "eslint-plugin-react-hooks": "^5.1.0-rc.0",
    "eslint-plugin-react-refresh": "^0.4.11",
    "globals": "^15.9.0",
    "postcss": "^8.4.35",
    "tailwindcss": "^3.4.1",
    "typescript": "^5.5.3",
    "typescript-eslint": "^8.3.0",
    "vite": "^5.4.2"
  }
}
<!doctype html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>WanderLust - Paquetes Turísticos Exclusivos</title>
    <meta name="description" content="Descubre el mundo con nuestros paquetes turísticos exclusivos. Experiencias únicas, destinos increíbles y aventuras inolvidables te esperan.">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import App from './App.tsx';
import './index.css';

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>
);
import React from 'react';
import Header from './components/Header';
import Hero from './components/Hero';
import FeaturedPackages from './components/FeaturedPackages';
import Destinations from './components/Destinations';
import Testimonials from './components/Testimonials';
import Contact from './components/Contact';
import Footer from './components/Footer';

function App() {
  return (
    <div className="min-h-screen">
      <Header />
      <Hero />
      <FeaturedPackages />
      <Destinations />
      <Testimonials />
      <Contact />
      <Footer />
    </div>
  );
}

export default App;
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');
@tailwind base;
@tailwind components;
@tailwind utilities;

* {
  font-family: 'Inter', sans-serif;
}

html {
  scroll-behavior: smooth;
}

body {
  line-height: 1.6;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f5f9;
}

::-webkit-scrollbar-thumb {
  background: #3b82f6;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #2563eb;
}

/* Smooth animations */
* {
  transition: color 0.2s ease, background-color 0.2s ease, border-color 0.2s ease, transform 0.2s ease, box-shadow 0.2s ease;
}

/* Enhanced button hover effects */
button {
  position: relative;
  overflow: hidden;
}

button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
  transition: left 0.5s;
}

button:hover::before {
  left: 100%;
}

/* Custom utilities */
.text-shadow {
  text-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.backdrop-blur-md {
  backdrop-filter: blur(12px);
}

/* Gradient animations */
@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.animate-gradient {
  background-size: 200% 200%;
  animation: gradient 3s ease infinite;
}
import React, { useState } from 'react';
import { Menu, X, MapPin, Phone, Mail } from 'lucide-react';

const Header = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);

  return (
    <header className="bg-white shadow-lg sticky top-0 z-50">
      {/* Top bar */}
      <div className="bg-gradient-to-r from-blue-600 to-teal-600 text-white py-2">
        <div className="max-w-7xl mx-auto px-4 flex justify-between items-center text-sm">
          <div className="flex items-center space-x-4">
            <div className="flex items-center space-x-1">
              <Phone className="w-4 h-4" />
              <span>+1 (555) 123-4567</span>
            </div>
            <div className="flex items-center space-x-1">
              <Mail className="w-4 h-4" />
              <span>info@wanderlust.com</span>
            </div>
          </div>
          <div className="hidden md:block">
            <span>¡Descuentos especiales hasta 30% OFF!</span>
          </div>
        </div>
      </div>

      {/* Main navigation */}
      <nav className="max-w-7xl mx-auto px-4 py-4">
        <div className="flex justify-between items-center">
          <div className="flex items-center space-x-2">
            <MapPin className="w-8 h-8 text-blue-600" />
            <h1 className="text-2xl font-bold text-gray-800">WanderLust</h1>
          </div>

          {/* Desktop menu */}
          <div className="hidden md:flex items-center space-x-8">
            <a href="#inicio" className="text-gray-700 hover:text-blue-600 transition-colors duration-200 font-medium">
              Inicio
            </a>
            <a href="#paquetes" className="text-gray-700 hover:text-blue-600 transition-colors duration-200 font-medium">
              Paquetes
            </a>
            <a href="#destinos" className="text-gray-700 hover:text-blue-600 transition-colors duration-200 font-medium">
              Destinos
            </a>
            <a href="#testimonios" className="text-gray-700 hover:text-blue-600 transition-colors duration-200 font-medium">
              Testimonios
            </a>
            <a href="#contacto" className="text-gray-700 hover:text-blue-600 transition-colors duration-200 font-medium">
              Contacto
            </a>
            <button className="bg-gradient-to-r from-blue-600 to-teal-600 text-white px-6 py-2 rounded-full hover:shadow-lg transform hover:scale-105 transition-all duration-200">
              Reservar Ahora
            </button>
          </div>

          {/* Mobile menu button */}
          <button
            className="md:hidden"
            onClick={() => setIsMenuOpen(!isMenuOpen)}
          >
            {isMenuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
          </button>
        </div>

        {/* Mobile menu */}
        {isMenuOpen && (
          <div className="md:hidden mt-4 pb-4 border-t pt-4">
            <div className="flex flex-col space-y-4">
              <a href="#inicio" className="text-gray-700 hover:text-blue-600 transition-colors">
                Inicio
              </a>
              <a href="#paquetes" className="text-gray-700 hover:text-blue-600 transition-colors">
                Paquetes
              </a>
              <a href="#destinos" className="text-gray-700 hover:text-blue-600 transition-colors">
                Destinos
              </a>
              <a href="#testimonios" className="text-gray-700 hover:text-blue-600 transition-colors">
                Testimonios
              </a>
              <a href="#contacto" className="text-gray-700 hover:text-blue-600 transition-colors">
                Contacto
              </a>
              <button className="bg-gradient-to-r from-blue-600 to-teal-600 text-white px-6 py-2 rounded-full w-full">
                Reservar Ahora
              </button>
            </div>
          </div>
        )}
      </nav>
    </header>
  );
};

export default Header;
import React from 'react';
import { Search, Calendar, Users, MapPin } from 'lucide-react';

const Hero = () => {
  return (
    <section id="inicio" className="relative min-h-screen flex items-center">
      {/* Background image */}
      <div className="absolute inset-0 z-0">
        <img
          src="https://images.pexels.com/photos/1591373/pexels-photo-1591373.jpeg?auto=compress&cs=tinysrgb&w=1920&h=1080&fit=crop"
          alt="Beautiful tropical destination"
          className="w-full h-full object-cover"
        />
        <div className="absolute inset-0 bg-gradient-to-r from-blue-900/70 to-teal-800/50"></div>
      </div>

      {/* Content */}
      <div className="relative z-10 max-w-7xl mx-auto px-4 text-white">
        <div className="grid lg:grid-cols-2 gap-12 items-center">
          {/* Left side - Hero text */}
          <div className="space-y-6">
            <h1 className="text-5xl lg:text-7xl font-bold leading-tight">
              Descubre el
              <span className="bg-gradient-to-r from-yellow-400 to-orange-400 bg-clip-text text-transparent block">
                Mundo
              </span>
              con Nosotros
            </h1>
            <p className="text-xl lg:text-2xl text-gray-200 leading-relaxed">
              Vive experiencias únicas con nuestros paquetes turísticos cuidadosamente diseñados. 
              Desde playas paradisíacas hasta montañas majestuosas.
            </p>
            <div className="flex flex-col sm:flex-row gap-4">
              <button className="bg-gradient-to-r from-yellow-400 to-orange-500 text-gray-900 px-8 py-4 rounded-full font-semibold text-lg hover:shadow-2xl transform hover:scale-105 transition-all duration-300">
                Explorar Paquetes
              </button>
              <button className="border-2 border-white text-white px-8 py-4 rounded-full font-semibold text-lg hover:bg-white hover:text-gray-900 transition-all duration-300">
                Ver Video
              </button>
            </div>
          </div>

          {/* Right side - Search form */}
          <div className="bg-white/95 backdrop-blur-md rounded-2xl p-8 shadow-2xl">
            <h3 className="text-2xl font-bold text-gray-800 mb-6">Encuentra tu próxima aventura</h3>
            <div className="space-y-4">
              <div className="relative">
                <MapPin className="absolute left-3 top-3 w-5 h-5 text-gray-400" />
                <input
                  type="text"
                  placeholder="¿A dónde quieres ir?"
                  className="w-full pl-10 pr-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-gray-800"
                />
              </div>
              
              <div className="grid grid-cols-2 gap-4">
                <div className="relative">
                  <Calendar className="absolute left-3 top-3 w-5 h-5 text-gray-400" />
                  <input
                    type="date"
                    className="w-full pl-10 pr-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-gray-800"
                  />
                </div>
                <div className="relative">
                  <Users className="absolute left-3 top-3 w-5 h-5 text-gray-400" />
                  <select className="w-full pl-10 pr-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-gray-800">
                    <option>1 Persona</option>
                    <option>2 Personas</option>
                    <option>3-4 Personas</option>
                    <option>5+ Personas</option>
                  </select>
                </div>
              </div>

              <button className="w-full bg-gradient-to-r from-blue-600 to-teal-600 text-white py-4 rounded-lg font-semibold text-lg hover:shadow-lg transform hover:scale-105 transition-all duration-200 flex items-center justify-center space-x-2">
                <Search className="w-5 h-5" />
                <span>Buscar Paquetes</span>
              </button>
            </div>
          </div>
        </div>
      </div>

      {/* Scroll indicator */}
      <div className="absolute bottom-8 left-1/2 transform -translate-x-1/2 text-white animate-bounce">
        <div className="w-6 h-10 border-2 border-white rounded-full flex justify-center">
          <div className="w-1 h-3 bg-white rounded-full mt-2 animate-pulse"></div>
        </div>
      </div>
    </section>
  );
};

export default Hero;
import React from 'react';
import { Star, Clock, Users, MapPin, Heart } from 'lucide-react';

const FeaturedPackages = () => {
  const packages = [
    {
      id: 1,
      title: "Bali Místico",
      subtitle: "Indonesia Paradisíaca",
      image: "https://images.pexels.com/photos/2474658/pexels-photo-2474658.jpeg?auto=compress&cs=tinysrgb&w=800&h=600&fit=crop",
      price: 1299,
      originalPrice: 1599,
      duration: "7 días",
      groupSize: "Max 12",
      rating: 4.9,
      reviews: 156,
      highlights: ["Templos sagrados", "Playas vírgenes", "Spa tradicional"],
      featured: true
    },
    {
      id: 2,
      title: "París Romántico",
      subtitle: "Francia Elegante",
      image: "https://images.pexels.com/photos/338515/pexels-photo-338515.jpeg?auto=compress&cs=tinysrgb&w=800&h=600&fit=crop",
      price: 899,
      originalPrice: 1199,
      duration: "5 días",
      groupSize: "Max 8",
      rating: 4.8,
      reviews: 203,
      highlights: ["Torre Eiffel", "Museo Louvre", "Crucero por Sena"]
    },
    {
      id: 3,
      title: "Tokio Futurista",
      subtitle: "Japón Moderno",
      image: "https://images.pexels.com/photos/2506923/pexels-photo-2506923.jpeg?auto=compress&cs=tinysrgb&w=800&h=600&fit=crop",
      price: 1599,
      originalPrice: 1899,
      duration: "8 días",
      groupSize: "Max 10",
      rating: 4.9,
      reviews: 127,
      highlights: ["Shibuya Crossing", "Monte Fuji", "Templos zen"]
    }
  ];

  return (
    <section className="py-20 bg-gradient-to-b from-gray-50 to-white">
      <div className="max-w-7xl mx-auto px-4">
        {/* Header */}
        <div className="text-center mb-16">
          <h2 className="text-4xl lg:text-5xl font-bold text-gray-800 mb-4">
            Paquetes <span className="text-blue-600">Destacados</span>
          </h2>
          <p className="text-xl text-gray-600 max-w-3xl mx-auto">
            Descubre nuestras experiencias más populares, cuidadosamente seleccionadas 
            para brindarte momentos inolvidables.
          </p>
        </div>

        {/* Packages grid */}
        <div className="grid lg:grid-cols-3 gap-8">
          {packages.map((pkg, index) => (
            <div 
              key={pkg.id} 
              className={`group relative bg-white rounded-2xl overflow-hidden shadow-lg hover:shadow-2xl transform hover:scale-105 transition-all duration-300 ${
                pkg.featured ? 'ring-4 ring-yellow-400 lg:scale-105' : ''
              }`}
            >
              {/* Featured badge */}
              {pkg.featured && (
                <div className="absolute top-4 left-4 bg-gradient-to-r from-yellow-400 to-orange-500 text-gray-900 px-3 py-1 rounded-full text-sm font-semibold z-10">
                  ⭐ Más Popular
                </div>
              )}

              {/* Heart icon */}
              <button className="absolute top-4 right-4 w-10 h-10 bg-white/90 rounded-full flex items-center justify-center hover:bg-white transition-colors z-10">
                <Heart className="w-5 h-5 text-gray-600 hover:text-red-500 transition-colors" />
              </button>

              {/* Image */}
              <div className="relative h-64 overflow-hidden">
                <img
                  src={pkg.image}
                  alt={pkg.title}
                  className="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
                />
                <div className="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent"></div>
                
                {/* Price badge */}
                <div className="absolute bottom-4 left-4 bg-white/95 backdrop-blur-sm rounded-lg px-3 py-2">
                  <div className="text-2xl font-bold text-gray-800">${pkg.price}</div>
                  <div className="text-sm text-gray-500 line-through">${pkg.originalPrice}</div>
                </div>
              </div>

              {/* Content */}
              <div className="p-6">
                <div className="flex items-center justify-between mb-2">
                  <h3 className="text-2xl font-bold text-gray-800">{pkg.title}</h3>
                  <div className="flex items-center space-x-1">
                    <Star className="w-4 h-4 fill-yellow-400 text-yellow-400" />
                    <span className="text-sm font-medium text-gray-600">{pkg.rating}</span>
                  </div>
                </div>

                <p className="text-blue-600 font-medium mb-4">{pkg.subtitle}</p>

                {/* Details */}
                <div className="flex items-center space-x-4 mb-4 text-sm text-gray-600">
                  <div className="flex items-center space-x-1">
                    <Clock className="w-4 h-4" />
                    <span>{pkg.duration}</span>
                  </div>
                  <div className="flex items-center space-x-1">
                    <Users className="w-4 h-4" />
                    <span>{pkg.groupSize}</span>
                  </div>
                  <div className="flex items-center space-x-1">
                    <span>{pkg.reviews} reseñas</span>
                  </div>
                </div>

                {/* Highlights */}
                <div className="mb-6">
                  <div className="flex flex-wrap gap-2">
                    {pkg.highlights.map((highlight, idx) => (
                      <span
                        key={idx}
                        className="bg-blue-50 text-blue-700 px-3 py-1 rounded-full text-sm"
                      >
                        {highlight}
                      </span>
                    ))}
                  </div>
                </div>

                {/* CTA Button */}
                <button className="w-full bg-gradient-to-r from-blue-600 to-teal-600 text-white py-3 rounded-lg font-semibold hover:shadow-lg transform hover:scale-105 transition-all duration-200">
                  Ver Detalles
                </button>
              </div>
            </div>
          ))}
        </div>

        {/* View all button */}
        <div className="text-center mt-12">
          <button className="bg-transparent border-2 border-blue-600 text-blue-600 px-8 py-4 rounded-full font-semibold text-lg hover:bg-blue-600 hover:text-white transition-all duration-300">
            Ver Todos los Paquetes
          </button>
        </div>
      </div>
    </section>
  );
};

export default FeaturedPackages;
import React from 'react';
import { MapPin, Plane } from 'lucide-react';

const Destinations = () => {
  const destinations = [
    {
      name: "Sudeste Asiático",
      countries: "Tailandia, Vietnam, Singapur",
      image: "https://images.pexels.com/photos/1658967/pexels-photo-1658967.jpeg?auto=compress&cs=tinysrgb&w=600&h=400&fit=crop",
      packages: 12
    },
    {
      name: "Europa Occidental",
      countries: "Francia, Italia, España",
      image: "https://images.pexels.com/photos/1386444/pexels-photo-1386444.jpeg?auto=compress&cs=tinysrgb&w=600&h=400&fit=crop",
      packages: 18
    },
    {
      name: "América del Sur",
      countries: "Perú, Chile, Argentina",
      image: "https://images.pexels.com/photos/2613260/pexels-photo-2613260.jpeg?auto=compress&cs=tinysrgb&w=600&h=400&fit=crop",
      packages: 8
    },
    {
      name: "África Oriental",
      countries: "Kenia, Tanzania, Uganda",
      image: "https://images.pexels.com/photos/631317/pexels-photo-631317.jpeg?auto=compress&cs=tinysrgb&w=600&h=400&fit=crop",
      packages: 6
    },
    {
      name: "Oceanía",
      countries: "Australia, Nueva Zelanda",
      image: "https://images.pexels.com/photos/1878293/pexels-photo-1878293.jpeg?auto=compress&cs=tinysrgb&w=600&h=400&fit=crop",
      packages: 10
    },
    {
      name: "Oriente Medio",
      countries: "Emiratos, Jordania, Turquía",
      image: "https://images.pexels.com/photos/3889855/pexels-photo-3889855.jpeg?auto=compress&cs=tinysrgb&w=600&h=400&fit=crop",
      packages: 7
    }
  ];

  return (
    <section id="destinos" className="py-20 bg-white">
      <div className="max-w-7xl mx-auto px-4">
        {/* Header */}
        <div className="text-center mb-16">
          <div className="flex items-center justify-center mb-4">
            <Plane className="w-8 h-8 text-blue-600 mr-3" />
            <h2 className="text-4xl lg:text-5xl font-bold text-gray-800">
              Destinos <span className="text-blue-600">Populares</span>
            </h2>
          </div>
          <p className="text-xl text-gray-600 max-w-3xl mx-auto">
            Explora los destinos más fascinantes del mundo con nuestros paquetes especializados
          </p>
        </div>

        {/* Destinations grid */}
        <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          {destinations.map((destination, index) => (
            <div
              key={index}
              className="group relative overflow-hidden rounded-2xl shadow-lg hover:shadow-2xl transform hover:scale-105 transition-all duration-300 cursor-pointer"
            >
              {/* Background image */}
              <div className="relative h-80">
                <img
                  src={destination.image}
                  alt={destination.name}
                  className="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
                />
                <div className="absolute inset-0 bg-gradient-to-t from-black/70 via-black/20 to-transparent"></div>
              </div>

              {/* Content overlay */}
              <div className="absolute inset-0 flex flex-col justify-end p-6 text-white">
                <div className="transform translate-y-2 group-hover:translate-y-0 transition-transform duration-300">
                  <h3 className="text-2xl font-bold mb-2">{destination.name}</h3>
                  <p className="text-gray-200 mb-3 flex items-center">
                    <MapPin className="w-4 h-4 mr-1" />
                    {destination.countries}
                  </p>
                  <div className="flex items-center justify-between">
                    <span className="bg-blue-600 text-white px-3 py-1 rounded-full text-sm font-medium">
                      {destination.packages} paquetes
                    </span>
                    <button className="opacity-0 group-hover:opacity-100 bg-white text-gray-800 px-4 py-2 rounded-full text-sm font-medium hover:bg-gray-100 transition-all duration-300">
                      Explorar
                    </button>
                  </div>
                </div>
              </div>

              {/* Hover effect overlay */}
              <div className="absolute inset-0 bg-blue-600/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            </div>
          ))}
        </div>

        {/* Stats section */}
        <div className="mt-20 bg-gradient-to-r from-blue-600 to-teal-600 rounded-2xl p-8 text-white">
          <div className="grid md:grid-cols-4 gap-8 text-center">
            <div>
              <div className="text-4xl font-bold mb-2">50+</div>
              <div className="text-blue-100">Destinos</div>
            </div>
            <div>
              <div className="text-4xl font-bold mb-2">10k+</div>
              <div className="text-blue-100">Viajeros Felices</div>
            </div>
            <div>
              <div className="text-4xl font-bold mb-2">15</div>
              <div className="text-blue-100">Años de Experiencia</div>
            </div>
            <div>
              <div className="text-4xl font-bold mb-2">24/7</div>
              <div className="text-blue-100">Soporte</div>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
};

export default Destinations;
import React from 'react';
import { Star, Quote } from 'lucide-react';

const Testimonials = () => {
  const testimonials = [
    {
      id: 1,
      name: "María González",
      location: "Madrid, España",
      image: "https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=150&h=150&fit=crop",
      rating: 5,
      text: "Mi viaje a Bali fue absolutamente mágico. Cada detalle fue perfectamente planificado y el servicio fue excepcional. WanderLust superó todas mis expectativas.",
      trip: "Bali Místico - 7 días"
    },
    {
      id: 2,
      name: "Carlos Rodríguez",
      location: "Buenos Aires, Argentina",
      image: "https://images.pexels.com/photos/1222271/pexels-photo-1222271.jpeg?auto=compress&cs=tinysrgb&w=150&h=150&fit=crop",
      rating: 5,
      text: "La experiencia en París fue increíble. Los guías locales, el itinerario y la atención al detalle hicieron que fuera el viaje perfecto para nuestra luna de miel.",
      trip: "París Romántico - 5 días"
    },
    {
      id: 3,
      name: "Ana Martínez",
      location: "México DF, México",
      image: "https://images.pexels.com/photos/415829/pexels-photo-415829.jpeg?auto=compress&cs=tinysrgb&w=150&h=150&fit=crop",
      rating: 5,
      text: "Tokio me fascinó completamente. La mezcla perfecta entre tradición y modernidad. WanderLust organizó cada momento para que fuera inolvidable.",
      trip: "Tokio Futurista - 8 días"
    },
    {
      id: 4,
      name: "Roberto Silva",
      location: "São Paulo, Brasil",
      image: "https://images.pexels.com/photos/1681010/pexels-photo-1681010.jpeg?auto=compress&cs=tinysrgb&w=150&h=150&fit=crop",
      rating: 5,
      text: "El safari en África fue la aventura de mi vida. Ver los Big Five en su hábitat natural fue emocionante. Recomiendo WanderLust al 100%.",
      trip: "Safari Africano - 10 días"
    }
  ];

  return (
    <section id="testimonios" className="py-20 bg-gradient-to-b from-gray-50 to-white">
      <div className="max-w-7xl mx-auto px-4">
        {/* Header */}
        <div className="text-center mb-16">
          <h2 className="text-4xl lg:text-5xl font-bold text-gray-800 mb-4">
            Lo que dicen nuestros <span className="text-blue-600">Viajeros</span>
          </h2>
          <p className="text-xl text-gray-600 max-w-3xl mx-auto">
            Miles de aventureros han confiado en nosotros para crear sus mejores recuerdos de viaje
          </p>
        </div>

        {/* Testimonials grid */}
        <div className="grid md:grid-cols-2 lg:grid-cols-2 gap-8 mb-12">
          {testimonials.map((testimonial) => (
            <div
              key={testimonial.id}
              className="bg-white rounded-2xl p-8 shadow-lg hover:shadow-2xl transform hover:scale-105 transition-all duration-300 relative"
            >
              {/* Quote icon */}
              <div className="absolute -top-4 left-8">
                <div className="bg-blue-600 p-3 rounded-full">
                  <Quote className="w-6 h-6 text-white" />
                </div>
              </div>

              {/* Content */}
              <div className="pt-4">
                {/* Rating */}
                <div className="flex items-center mb-4">
                  {[...Array(testimonial.rating)].map((_, i) => (
                    <Star key={i} className="w-5 h-5 fill-yellow-400 text-yellow-400" />
                  ))}
                </div>

                {/* Text */}
                <p className="text-gray-700 text-lg leading-relaxed mb-6 italic">
                  "{testimonial.text}"
                </p>

                {/* Trip info */}
                <div className="bg-blue-50 rounded-lg p-3 mb-6">
                  <p className="text-blue-700 font-medium text-sm">{testimonial.trip}</p>
                </div>

                {/* Author */}
                <div className="flex items-center">
                  <img
                    src={testimonial.image}
                    alt={testimonial.name}
                    className="w-12 h-12 rounded-full object-cover mr-4"
                  />
                  <div>
                    <h4 className="font-semibold text-gray-800">{testimonial.name}</h4>
                    <p className="text-gray-600 text-sm">{testimonial.location}</p>
                  </div>
                </div>
              </div>
            </div>
          ))}
        </div>

        {/* Trust indicators */}
        <div className="bg-white rounded-2xl p-8 shadow-lg">
          <div className="grid md:grid-cols-3 gap-8 text-center">
            <div>
              <div className="flex items-center justify-center mb-4">
                {[...Array(5)].map((_, i) => (
                  <Star key={i} className="w-6 h-6 fill-yellow-400 text-yellow-400" />
                ))}
              </div>
              <h3 className="text-2xl font-bold text-gray-800 mb-2">4.9/5</h3>
              <p className="text-gray-600">Calificación promedio</p>
            </div>
            <div>
              <h3 className="text-2xl font-bold text-gray-800 mb-2">98%</h3>
              <p className="text-gray-600">Clientes satisfechos</p>
            </div>
            <div>
              <h3 className="text-2xl font-bold text-gray-800 mb-2">1,247</h3>
              <p className="text-gray-600">Reseñas verificadas</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
};

export default Testimonials;
import React, { useState } from 'react';
import { Mail, Phone, MapPin, Send, Clock, Award, Shield, HeartHandshake } from 'lucide-react';

const Contact = () => {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    phone: '',
    destination: '',
    travelers: '',
    budget: '',
    message: ''
  });

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    // Handle form submission here
    console.log('Form submitted:', formData);
  };

  const handleChange = (e: React.ChangeEvent<HTMLInputElement | HTMLSelectElement | HTMLTextAreaElement>) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };

  return (
    <section id="contacto" className="py-20 bg-gradient-to-b from-white to-gray-50">
      <div className="max-w-7xl mx-auto px-4">
        {/* Header */}
        <div className="text-center mb-16">
          <h2 className="text-4xl lg:text-5xl font-bold text-gray-800 mb-4">
            Planifiquemos tu próxima <span className="text-blue-600">Aventura</span>
          </h2>
          <p className="text-xl text-gray-600 max-w-3xl mx-auto">
            Nuestros expertos en viajes están listos para crear la experiencia perfecta para ti
          </p>
        </div>

        <div className="grid lg:grid-cols-2 gap-12">
          {/* Contact form */}
          <div className="bg-white rounded-2xl p-8 shadow-lg">
            <h3 className="text-2xl font-bold text-gray-800 mb-6">Solicita tu cotización personalizada</h3>
            
            <form onSubmit={handleSubmit} className="space-y-6">
              <div className="grid md:grid-cols-2 gap-4">
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">
                    Nombre completo *
                  </label>
                  <input
                    type="text"
                    name="name"
                    value={formData.name}
                    onChange={handleChange}
                    required
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                    placeholder="Tu nombre"
                  />
                </div>
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">
                    Email *
                  </label>
                  <input
                    type="email"
                    name="email"
                    value={formData.email}
                    onChange={handleChange}
                    required
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                    placeholder="tu@email.com"
                  />
                </div>
              </div>

              <div className="grid md:grid-cols-2 gap-4">
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">
                    Teléfono
                  </label>
                  <input
                    type="tel"
                    name="phone"
                    value={formData.phone}
                    onChange={handleChange}
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                    placeholder="(555) 123-4567"
                  />
                </div>
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">
                    Destino de interés
                  </label>
                  <select
                    name="destination"
                    value={formData.destination}
                    onChange={handleChange}
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                  >
                    <option value="">Selecciona un destino</option>
                    <option value="bali">Bali, Indonesia</option>
                    <option value="paris">París, Francia</option>
                    <option value="tokyo">Tokio, Japón</option>
                    <option value="africa">Safari Africano</option>
                    <option value="other">Otro destino</option>
                  </select>
                </div>
              </div>

              <div className="grid md:grid-cols-2 gap-4">
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">
                    Número de viajeros
                  </label>
                  <select
                    name="travelers"
                    value={formData.travelers}
                    onChange={handleChange}
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                  >
                    <option value="">Selecciona</option>
                    <option value="1">1 persona</option>
                    <option value="2">2 personas</option>
                    <option value="3-4">3-4 personas</option>
                    <option value="5+">5+ personas</option>
                  </select>
                </div>
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-2">
                    Presupuesto aproximado
                  </label>
                  <select
                    name="budget"
                    value={formData.budget}
                    onChange={handleChange}
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                  >
                    <option value="">Selecciona</option>
                    <option value="500-1000">$500 - $1,000</option>
                    <option value="1000-2000">$1,000 - $2,000</option>
                    <option value="2000-5000">$2,000 - $5,000</option>
                    <option value="5000+">$5,000+</option>
                  </select>
                </div>
              </div>

              <div>
                <label className="block text-sm font-medium text-gray-700 mb-2">
                  Cuéntanos sobre tu viaje ideal
                </label>
                <textarea
                  name="message"
                  value={formData.message}
                  onChange={handleChange}
                  rows={4}
                  className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                  placeholder="Describe tus intereses, fechas preferidas, tipo de experiencias..."
                ></textarea>
              </div>

              <button
                type="submit"
                className="w-full bg-gradient-to-r from-blue-600 to-teal-600 text-white py-4 rounded-lg font-semibold text-lg hover:shadow-lg transform hover:scale-105 transition-all duration-200 flex items-center justify-center space-x-2"
              >
                <Send className="w-5 h-5" />
                <span>Enviar Solicitud</span>
              </button>
            </form>
          </div>

          {/* Contact info and features */}
          <div className="space-y-8">
            {/* Contact details */}
            <div className="bg-gradient-to-r from-blue-600 to-teal-600 rounded-2xl p-8 text-white">
              <h3 className="text-2xl font-bold mb-6">Contáctanos directamente</h3>
              
              <div className="space-y-4">
                <div className="flex items-center space-x-3">
                  <Phone className="w-6 h-6" />
                  <div>
                    <p className="font-medium">Teléfono</p>
                    <p className="text-blue-100">+1 (555) 123-4567</p>
                  </div>
                </div>
                
                <div className="flex items-center space-x-3">
                  <Mail className="w-6 h-6" />
                  <div>
                    <p className="font-medium">Email</p>
                    <p className="text-blue-100">info@wanderlust.com</p>
                  </div>
                </div>
                
                <div className="flex items-center space-x-3">
                  <MapPin className="w-6 h-6" />
                  <div>
                    <p className="font-medium">Oficina</p>
                    <p className="text-blue-100">123 Travel Street, Miami, FL 33101</p>
                  </div>
                </div>
                
                <div className="flex items-center space-x-3">
                  <Clock className="w-6 h-6" />
                  <div>
                    <p className="font-medium">Horarios</p>
                    <p className="text-blue-100">Lun - Vie: 9AM - 8PM</p>
                    <p className="text-blue-100">Sáb - Dom: 10AM - 6PM</p>
                  </div>
                </div>
              </div>
            </div>

            {/* Why choose us */}
            <div className="bg-white rounded-2xl p-8 shadow-lg">
              <h3 className="text-2xl font-bold text-gray-800 mb-6">¿Por qué elegirnos?</h3>
              
              <div className="space-y-4">
                <div className="flex items-start space-x-3">
                  <Award className="w-6 h-6 text-blue-600 mt-1" />
                  <div>
                    <h4 className="font-semibold text-gray-800">15 años de experiencia</h4>
                    <p className="text-gray-600 text-sm">Expertos en crear experiencias únicas</p>
                  </div>
                </div>
                
                <div className="flex items-start space-x-3">
                  <Shield className="w-6 h-6 text-blue-600 mt-1" />
                  <div>
                    <h4 className="font-semibold text-gray-800">Viajes seguros</h4>
                    <p className="text-gray-600 text-sm">Protección completa y seguro incluido</p>
                  </div>
                </div>
                
                <div className="flex items-start space-x-3">
                  <HeartHandshake className="w-6 h-6 text-blue-600 mt-1" />
                  <div>
                    <h4 className="font-semibold text-gray-800">Atención personalizada</h4>
                    <p className="text-gray-600 text-sm">Soporte 24/7 durante tu viaje</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
};

export default Contact;
import React from 'react';
import { MapPin, Phone, Mail, Facebook, Instagram, Twitter, Youtube, Heart } from 'lucide-react';

const Footer = () => {
  return (
    <footer className="bg-gray-900 text-white">
      {/* Main footer content */}
      <div className="max-w-7xl mx-auto px-4 py-16">
        <div className="grid lg:grid-cols-4 md:grid-cols-2 gap-8">
          {/* Company info */}
          <div className="lg:col-span-1">
            <div className="flex items-center space-x-2 mb-4">
              <MapPin className="w-8 h-8 text-blue-400" />
              <h3 className="text-2xl font-bold">WanderLust</h3>
            </div>
            <p className="text-gray-300 mb-6 leading-relaxed">
              Creamos experiencias de viaje inolvidables que conectan a las personas con las culturas, 
              paisajes y aventuras más increíbles del mundo.
            </p>
            <div className="flex space-x-4">
              <a href="#" className="bg-blue-600 p-2 rounded-full hover:bg-blue-700 transition-colors">
                <Facebook className="w-5 h-5" />
              </a>
              <a href="#" className="bg-pink-600 p-2 rounded-full hover:bg-pink-700 transition-colors">
                <Instagram className="w-5 h-5" />
              </a>
              <a href="#" className="bg-blue-400 p-2 rounded-full hover:bg-blue-500 transition-colors">
                <Twitter className="w-5 h-5" />
              </a>
              <a href="#" className="bg-red-600 p-2 rounded-full hover:bg-red-700 transition-colors">
                <Youtube className="w-5 h-5" />
              </a>
            </div>
          </div>

          {/* Quick links */}
          <div>
            <h4 className="text-lg font-semibold mb-4">Enlaces Rápidos</h4>
            <ul className="space-y-2">
              <li><a href="#inicio" className="text-gray-300 hover:text-white transition-colors">Inicio</a></li>
              <li><a href="#paquetes" className="text-gray-300 hover:text-white transition-colors">Paquetes</a></li>
              <li><a href="#destinos" className="text-gray-300 hover:text-white transition-colors">Destinos</a></li>
              <li><a href="#testimonios" className="text-gray-300 hover:text-white transition-colors">Testimonios</a></li>
              <li><a href="#contacto" className="text-gray-300 hover:text-white transition-colors">Contacto</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Blog de Viajes</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Ofertas Especiales</a></li>
            </ul>
          </div>

          {/* Destinations */}
          <div>
            <h4 className="text-lg font-semibold mb-4">Destinos Populares</h4>
            <ul className="space-y-2">
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Bali, Indonesia</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">París, Francia</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Tokio, Japón</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Safari Africano</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Machu Picchu, Perú</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Santorini, Grecia</a></li>
              <li><a href="#" className="text-gray-300 hover:text-white transition-colors">Islas Maldivas</a></li>
            </ul>
          </div>

          {/* Contact info */}
          <div>
            <h4 className="text-lg font-semibold mb-4">Información de Contacto</h4>
            <div className="space-y-3">
              <div className="flex items-start space-x-3">
                <MapPin className="w-5 h-5 text-blue-400 mt-1" />
                <div>
                  <p className="text-gray-300">123 Travel Street</p>
                  <p className="text-gray-300">Miami, FL 33101</p>
                </div>
              </div>
              <div className="flex items-center space-x-3">
                <Phone className="w-5 h-5 text-blue-400" />
                <p className="text-gray-300">+1 (555) 123-4567</p>
              </div>
              <div className="flex items-center space-x-3">
                <Mail className="w-5 h-5 text-blue-400" />
                <p className="text-gray-300">info@wanderlust.com</p>
              </div>
            </div>

            {/* Newsletter */}
            <div className="mt-6">
              <h5 className="font-semibold mb-3">Suscríbete a nuestro newsletter</h5>
              <div className="flex">
                <input
                  type="email"
                  placeholder="Tu email"
                  className="flex-1 px-3 py-2 bg-gray-800 border border-gray-700 rounded-l-lg focus:outline-none focus:border-blue-400"
                />
                <button className="bg-blue-600 px-4 py-2 rounded-r-lg hover:bg-blue-700 transition-colors">
                  <Mail className="w-4 h-4" />
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>

      {/* Bottom bar */}
      <div className="border-t border-gray-800">
        <div className="max-w-7xl mx-auto px-4 py-6">
          <div className="flex flex-col md:flex-row justify-between items-center">
            <div className="flex items-center space-x-4 mb-4 md:mb-0">
              <p className="text-gray-400">© 2024 WanderLust. Todos los derechos reservados.</p>
            </div>
            <div className="flex items-center space-x-6">
              <a href="#" className="text-gray-400 hover:text-white transition-colors text-sm">
                Política de Privacidad
              </a>
              <a href="#" className="text-gray-400 hover:text-white transition-colors text-sm">
                Términos de Servicio
              </a>
              <a href="#" className="text-gray-400 hover:text-white transition-colors text-sm">
                Cookies
              </a>
            </div>
          </div>
          <div className="flex items-center justify-center mt-4 text-gray-400 text-sm">
            <span>Hecho con</span>
            <Heart className="w-4 h-4 text-red-500 mx-1 fill-current" />
            <span>para viajeros aventureros</span>
          </div>
        </div>
      </div>
    </footer>
  );
};

export default Footer;
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {},
  },
  plugins: [],
};
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  optimizeDeps: {
    exclude: ['lucide-react'],
  },
});
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};
{
  "files": [],
  "references": [
    { "path": "./tsconfig.app.json" },
    { "path": "./tsconfig.node.json" }
  ]
}
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,

    /* Bundler mode */
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "isolatedModules": true,
    "moduleDetection": "force",
    "noEmit": true,
    "jsx": "react-jsx",

    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["src"]
}
{
  "compilerOptions": {
    "target": "ES2022",
    "lib": ["ES2023"],
    "module": "ESNext",
    "skipLibCheck": true,

    /* Bundler mode */
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "isolatedModules": true,
    "moduleDetection": "force",
    "noEmit": true,

    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["vite.config.ts"]
}
import js from '@eslint/js';
import globals from 'globals';
import reactHooks from 'eslint-plugin-react-hooks';
import reactRefresh from 'eslint-plugin-react-refresh';
import tseslint from 'typescript-eslint';

export default tseslint.config(
  { ignores: ['dist'] },
  {
    extends: [js.configs.recommended, ...tseslint.configs.recommended],
    files: ['**/*.{ts,tsx}'],
    languageOptions: {
      ecmaVersion: 2020,
      globals: globals.browser,
    },
    plugins: {
      'react-hooks': reactHooks,
      'react-refresh': reactRefresh,
    },
    rules: {
      ...reactHooks.configs.recommended.rules,
      'react-refresh/only-export-components': [
        'warn',
        { allowConstantExport: true },
      ],
    },
  }
);
/// <reference types="vite/client" />

