## Hi there 👋

<!--
**Rexona7/Rexona7** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biblioteca Digital - Gestión de Recursos</title>
	
    <!-- Importar TailwindCSS -->
    <script src="https://cdn.tailwindcss.com"></script>
	
    <!-- Importar Font Awesome para iconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
	<!-- Estilos personalizados -->
    <style>
        /* Estilos para el modal */
        .modal {
            transition: opacity 0.3s ease, transform 0.3s ease;
            transform: translateY(-20px);
            opacity: 0;
        }
        .modal.active {
            transform: translateY(0);
            opacity: 1;
        }
        
        /* Estilos para la barra de búsqueda */
        .search-container {
            transition: all 0.3s ease;
        }
        .search-container.focused {
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        /* Animación para los cards de libros */
        .book-card {
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }
        .book-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        /* Estilos para el menú móvil */
        .mobile-menu {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
        }
        .mobile-menu.open {
            max-height: 500px;
        }
    </style>
</head>
<body class="bg-gray-900 font-sans">
    <!-- Barra de navegación -->
    <nav class="bg-red-800 text-white shadow-lg">
        <div class="container mx-auto px-4 py-3">
            <div class="flex justify-between items-center">
                <!-- Logo y nombre del sitio -->
                <div class="flex items-center space-x-2">
                    <i class="fas fa-book-open text-2xl"></i>
                    <span class="text-xl font-bold">Mate con Libritos</span>
                </div>
                

				
				<div class="hidden md:flex space-x-6">
					<a href="index.html" class="hover:text-black transition" id="home-link">Inicio</a> 
					<a href="catalogo.html" class="hover:text-black transition" id="catalog-link">Catálogo</a>
					<a href="prestamos.html" class="hover:text-black transition" id="loans-link">Préstamos</a>
					<a href="eventos.html" class="hover:text-black transition" id="events-link">Eventos</a>
					<a href="crear.html" class="hover:text-black transition" id="admin-link">Crear</a>
				</div>

                
                <!-- Botones de usuario -->
                <div class="hidden md:flex items-center space-x-4">
                    <button class="bg-red-800 hover:bg-blue-800 px-4 py-2 rounded transition" id="login-btn">
                        <i class="fas fa-sign-in-alt mr-2"></i>Iniciar sesión login_form
						<a href="login_form" target="_blank"></a>
                    </button>
                    <button class="bg-bl-600-800 hover:bg-blue-600 px-4 py-2 rounded transition" id="register-btn">
                        <i class="fas fa-user-plus mr-2"></i>Registrarse
						<a href="user_registration_form" target="_blank"></a>
                    </button>
                </div>
                
           
            <!--Menú  (oculto por defecto)-->
            <div class="mobile-menu md:hidden bg-blue-800 mt-2 rounded-lg" id="mobile-menu">
                <div class="flex flex-col space-y-3 p-4">
                    <a href="#" class="hover:text-blue-200 transition">Inicio</a>
                    <a href="#" class="hover:text-blue-200 transition">Catálogo</a>
                    <a href="#" class="hover:text-blue-200 transition">Préstamos</a>
                    <a href="#" class="hover:text-blue-200 transition">Eventos</a>
                    <a href="#" class="hover:text-blue-200 transition">Crear</a>
                    <div class="border-t border-blue-600 pt-2">
                        <button class="w-full bg-blue-600 hover:bg-blue-800 px-4 py-2 rounded transition mb-2">
                            <i class="fas fa-sign-in-alt mr-2"></i>Iniciar sesión
                        </button>
                        <button class="w-full bg-green-600 hover:bg-green-800 px-4 py-2 rounded transition">
                            <i class="fas fa-user-plus mr-2"></i>Registrarse
                        </button>
                    </div>
                </div>
            </div> 
        </div>
    </nav>  

    <!-- Contenido principal -->
    <main class="container mx-auto px-4 py-8">
        <!-- Sección de bienvenida -->
        <section class="mb-12 text-center">
            <h1 class="text-4xl font-bold text-white mb-4">Pasá a nuestra librería digital. Los libros están listos, el mate también.</h1>
            <p class="text-lg text-gray-700 max-w-3xl mx-auto">
                Accede a nuestro extenso catálogo de recursos bibliográficos, gestiona tus préstamos y mantente al día con los últimos eventos y novedades.
            </p>  
        </section>
        
        <!-- Barra de búsqueda -->
        <section class="mb-12">
            <div class="max-w-3xl mx-auto search-container bg-white rounded-lg shadow-md p-2 border border-gray-200" id="search-container">
                <div class="flex">
                    <input 
                        type="text" 
                        placeholder="Buscar libros, autores, temas..." 
                        class="flex-grow px-4 py-3 focus:outline-none rounded-l"
                        id="search-input"
                    >
                    <button class="bg-blue-600 hover:bg-blue-800 text-white px-6 py-3 rounded-r transition">
                        <i class="fas fa-search"></i>
                    </button>
                </div>
				
                <div class="mt-2 hidden" id="search-suggestions">
                    <div class="bg-white border border-gray-200 rounded shadow-lg p-2">
                        <p class="text-sm text-gray-500 px-2 py-1">Sugerencias:</p>
                        <a href="#" class="block px-2 py-1 hover:bg-gray-100 rounded">Matemáticas avanzadas</a>
                        <a href="#" class="block px-2 py-1 hover:bg-gray-100 rounded">Historia del arte</a>
                        <a href="#" class="block px-2 py-1 hover:bg-gray-100 rounded">Programación JavaScript</a>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Sección de categorías -->
        <section class="mb-12">
            <h2 class="text-2xl font-bold text-blue-600 mb-6">Explora por categorías</h2>
            <div class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-4">
                <div class="bg-white p-4 rounded-lg shadow-md text-center hover:bg-blue-50 transition cursor-pointer">
                    <i class="fas fa-flask text-3xl text-blue-600 mb-2"></i>
                    <p class="font-medium">Ciencias</p>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-md text-center hover:bg-blue-50 transition cursor-pointer">
                    <i class="fas fa-laptop-code text-3xl text-blue-600 mb-2"></i>
                    <p class="font-medium">Tecnología</p>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-md text-center hover:bg-blue-50 transition cursor-pointer">
                    <i class="fas fa-book text-3xl text-blue-600 mb-2"></i>
                    <p class="font-medium">Literatura</p>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-md text-center hover:bg-blue-50 transition cursor-pointer">
                    <i class="fas fa-landmark text-3xl text-blue-600 mb-2"></i>
                    <p class="font-medium">Historia</p>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-md text-center hover:bg-blue-50 transition cursor-pointer">
                    <i class="fas fa-paint-brush text-3xl text-blue-600 mb-2"></i>
                    <p class="font-medium">Arte</p>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-md text-center hover:bg-blue-50 transition cursor-pointer">
                    <i class="fas fa-globe-americas text-3xl text-blue-600 mb-2"></i>
                    <p class="font-medium">Idiomas</p>
                </div>
            </div>
        </section>
        
        <!-- Sección de libros destacados -->
        <section class="mb-12">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-blue-600">Libros destacados</h2>
                <a href="#" class="text-blue-600 hover:underline">Ver todos</a>
            </div>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                <!-- Libro 1 -->
                <div class="book-card bg-white rounded-lg shadow-md overflow-hidden">
                    <div class="h-48 bg-blue-100 flex items-center justify-center">
                        <i class="fas fa-book-open text-5xl text-blue-600"></i>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-lg mb-1">Introducción a la Programación</h3>
                        <p class="text-gray-600 text-sm mb-2">Autor: John Doe</p>
                        <div class="flex justify-between items-center">
                            <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">Disponible</span>
                            <button class="text-blue-600 hover:text-blue-800">
                                <i class="fas fa-plus-circle"></i> Reservar
                            </button>
                        </div>
                    </div>
                </div>
                
                <!-- Libro 2 -->
                <div class="book-card bg-white rounded-lg shadow-md overflow-hidden">
                    <div class="h-48 bg-green-100 flex items-center justify-center">
                        <i class="fas fa-book-open text-5xl text-green-600"></i>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-lg mb-1">Historia del Arte Moderno</h3>
                        <p class="text-gray-600 text-sm mb-2">Autor: Jane Smith</p>
                        <div class="flex justify-between items-center">
                            <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Disponible</span>
                            <button class="text-blue-600 hover:text-blue-800">
                                <i class="fas fa-plus-circle"></i> Reservar
                            </button>
                        </div>
                    </div>
                </div>
                
                <!-- Libro 3 -->
                <div class="book-card bg-white rounded-lg shadow-md overflow-hidden">
                    <div class="h-48 bg-yellow-100 flex items-center justify-center">
                        <i class="fas fa-book-open text-5xl text-yellow-600"></i>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-lg mb-1">Matemáticas Avanzadas</h3>
                        <p class="text-gray-600 text-sm mb-2">Autor: Robert Johnson</p>
                        <div class="flex justify-between items-center">
                            <span class="bg-red-100 text-red-800 text-xs px-2 py-1 rounded">Prestado</span>
                            <button class="text-gray-400 cursor-not-allowed" disabled>
                                <i class="fas fa-plus-circle"></i> Reservar
                            </button>
                        </div>
                    </div>
                </div>
                
                <!-- Libro 4 -->
                <div class="book-card bg-white rounded-lg shadow-md overflow-hidden">
                    <div class="h-48 bg-purple-100 flex items-center justify-center">
                        <i class="fas fa-book-open text-5xl text-purple-600"></i>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-lg mb-1">Física Cuántica</h3>
                        <p class="text-gray-600 text-sm mb-2">Autor: María García</p>
                        <div class="flex justify-between items-center">
                            <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">Disponible</span>
                            <button class="text-blue-600 hover:text-blue-800">
                                <i class="fas fa-plus-circle"></i> Reservar
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Sección de eventos -->
        <section class="mb-12">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-blue-600">Próximos eventos</h2>
                <a href="#" class="text-blue-600 hover:underline">Ver todos</a>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Evento 1 -->
                <div class="bg-white rounded-lg shadow-md overflow-hidden">
                    <div class="h-40 bg-blue-600 flex items-center justify-center text-white">
                        <i class="fas fa-calendar-alt text-5xl"></i>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-lg">Club de lectura</h3>
                            <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">15 Mayo</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">Únete a nuestro club de lectura mensual donde discutiremos el libro seleccionado.</p>
                        <button class="w-full bg-blue-600 hover:bg-blue-800 text-white py-2 rounded transition">
                            Más información
                        </button>
                    </div>
                </div>
                
                <!-- Evento 2 -->
                <div class="bg-white rounded-lg shadow-md overflow-hidden">
                    <div class="h-40 bg-green-600 flex items-center justify-center text-white">
                        <i class="fas fa-graduation-cap text-5xl"></i>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-lg">Taller de investigación</h3>
                            <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">22 Mayo</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">Aprende técnicas avanzadas de investigación académica con nuestros expertos.</p>
                        <button class="w-full bg-green-600 hover:bg-green-800 text-white py-2 rounded transition">
                            Más información
                        </button>
                    </div>
                </div>
                
                <!-- Evento 3 -->
                <div class="bg-white rounded-lg shadow-md overflow-hidden">
                    <div class="h-40 bg-purple-600 flex items-center justify-center text-white">
                        <i class="fas fa-laptop text-5xl"></i>
                    </div>
                    <div class="p-4">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-lg">Introducción a Python</h3>
                            <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">30 Mayo</span>
                        </div>
                        <p class="text-gray-600 text-sm mb-3">Taller práctico para aprender los fundamentos del lenguaje de programación Python.</p>
                        <button class="w-full bg-purple-600 hover:bg-purple-800 text-white py-2 rounded transition">
                            Más información
                        </button>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Pie de página -->
    <footer class="bg-gray-800 text-white py-8">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                <!-- Columna 1 -->
                <div>
                    <h3 class="text-xl font-bold mb-4">Biblioteca Digital</h3>
                    <p class="text-gray-400">
                        Tu centro de recursos académicos en línea. Accede a miles de libros, gestiona tus préstamos y participa en nuestros eventos.
                    </p>
                </div>
                
                <!-- Columna 2 -->
                <div>
                    <h3 class="text-xl font-bold mb-4">Enlaces rápidos</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Inicio</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Catálogo</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Préstamos</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Eventos</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition">Contacto</a></li>
                    </ul>
                </div>
                
                <!-- Columna 3 -->
                <div>
                    <h3 class="text-xl font-bold mb-4">Contacto</h3>
                    <ul class="space-y-2 text-gray-400">
                        <li class="flex items-center">
                            <i class="fas fa-map-marker-alt mr-2"></i> Av. Universidad 123, Ciudad
                        </li>
                        <li class="flex items-center">
                            <i class="fas fa-phone mr-2"></i> (123) 456-7890
                        </li>
                        <li class="flex items-center">
                            <i class="fas fa-envelope mr-2"></i> contacto@bibliotecadigital.edu
                        </li>
                    </ul>
                </div>
                
                <!-- Columna 4 -->
                <div>
                    <h3 class="text-xl font-bold mb-4">Síguenos</h3>
                    <div class="flex space-x-4">
                        <a href="#" class="text-gray-400 hover:text-white transition text-2xl">
                            <i class="fab fa-facebook"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition text-2xl">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition text-2xl">
                            <i class="fab fa-instagram"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition text-2xl">
                            <i class="fab fa-youtube"></i>
                        </a>
                    </div>
                    
                    <h3 class="text-xl font-bold mt-6 mb-4">Suscríbete</h3>
                    <div class="flex">
                        <input 
                            type="email" 
                            placeholder="Tu correo" 
                            class="flex-grow px-3 py-2 bg-gray-700 text-white focus:outline-none rounded-l"
                        >
                        <button class="bg-blue-600 hover:bg-blue-800 px-4 py-2 rounded-r transition">
                            <i class="fas fa-paper-plane"></i>
                        </button>
                    </div>
                </div>
            </div>
            
            <div class="border-t border-gray-700 mt-8 pt-6 text-center text-gray-400">
                <p>&copy; 2025 Biblioteca Digital. Todos los derechos reservados.</p>
            </div>
        </div>
    </footer>

    <!-- Modal de inicio de sesión -->
    <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 hidden" id="login-modal">
        <div class="modal bg-white rounded-lg shadow-xl w-full max-w-md">
            <div class="p-6">
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-2xl font-bold text-blue-800">Iniciar sesión</h3>
                    <button class="text-gray-500 hover:text-gray-700" id="close-login-modal">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
                
                <form id="login-form">
                    <div class="mb-4">
                        <label for="login-email" class="block text-gray-700 mb-2">Correo electrónico</label>
                        <input 
                            type="email" 
                            id="login-email" 
                            class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
                            required
                        >
                    </div>
                    
                    <div class="mb-6">
                        <label for="login-password" class="block text-gray-700 mb-2">Contraseña</label>
                        <input 
                            type="password" 
                            id="login-password" 
                            class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
                            required
                        >
                        <a href="#" class="text-sm text-blue-600 hover:underline mt-1 block">¿Olvidaste tu contraseña?</a>
                    </div>
                    
                    <div class="flex items-center mb-4">
                        <input 
                            type="checkbox" 
                            id="remember-me" 
                            class="mr-2"
                        >
                        <label for="remember-me" class="text-gray-700">Recordarme</label>
                    </div>
                    
                    <button type="submit" class="w-full bg-blue-600 hover:bg-blue-800 text-white py-2 px-4 rounded transition mb-4">
                        Iniciar sesión
                    </button>
                    
                    <p class="text-center text-gray-600">
                        ¿No tienes una cuenta? 
                        <a href="#" class="text-blue-600 hover:underline" id="show-register-from-login">Regístrate</a>
                    </p>
                </form>
            </div>
        </div>
    </div>

    <!-- Modal de registro -->
    <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 hidden" id="register-modal">
        <div class="modal bg-white rounded-lg shadow-xl w-full max-w-md">
            <div class="p-6">
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-2xl font-bold text-blue-800">Registrarse</h3>
                    <button class="text-gray-500 hover:text-gray-700" id="close-register-modal">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
                
                <form id="register-form">
                    <div class="mb-4">
                        <label for="register-name" class="block text-gray-700 mb-2">Nombre completo</label>
                        <input 
                            type="text" 
                            id="register-name" 
                            class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
                            required
                        >
                    </div>
                    
                    <div class="mb-4">
                        <label for="register-email" class="block text-gray-700 mb-2">Correo electrónico</label>
                        <input 
                            type="email" 
                            id="register-email" 
                            class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
                            required
                        >
                    </div>
                    
                    <div class="mb-4">
                        <label for="register-password" class="block text-gray-700 mb-2">Contraseña</label>
                        <input 
                            type="password" 
                            id="register-password" 
                            class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
                            required
                        >
                    </div>
                    
                    <div class="mb-6">
                        <label for="register-confirm-password" class="block text-gray-700 mb-2">Confirmar contraseña</label>
                        <input 
                            type="password" 
                            id="register-confirm-password" 
                            class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
                            required
                        >
                    </div>
                    
                    <div class="mb-4">
                        <label for="register-role" class="block text-gray-700 mb-2">Tipo de usuario</label>
                        <select 
                            id="register-role" 
                            class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
                            required
                        >
                            <option value="">Selecciona una opción</option>
                            <option value="student">Estudiante</option>
                            <option value="teacher">Profesor</option>
                            <option value="staff">Personal de biblioteca</option>
                        </select>
                    </div>
                    
                    <div class="flex items-center mb-4">
                        <input 
                            type="checkbox" 
                            id="terms" 
                            class="mr-2"
                            required
                        >
                        <label for="terms" class="text-gray-700">
                            Acepto los <a href="#" class="text-blue-600 hover:underline">términos y condiciones</a>
                        </label>
                    </div>
                    
                    <button type="submit" class="w-full bg-green-600 hover:bg-green-800 text-white py-2 px-4 rounded transition mb-4">
                        Registrarse
                    </button>
                    
                    <p class="text-center text-gray-600">
                        ¿Ya tienes una cuenta? 
                        <a href="#" class="text-blue-600 hover:underline" id="show-login-from-register">Inicia sesión</a>
                    </p>
                </form>
            </div>
        </div>
    </div>

    <!-- Scripts JavaScript -->
    <script>
        // Documentación: Este script maneja toda la interactividad del sitio web
        
        // Esperar a que el DOM esté completamente cargado
        document.addEventListener('DOMContentLoaded', function() {
            // Elementos del DOM
            const mobileMenuBtn = document.getElementById('mobile-menu-btn');
            const mobileMenu = document.getElementById('mobile-menu');
            const loginBtn = document.getElementById('login-btn');
            const registerBtn = document.getElementById('register-btn');
            const loginModal = document.getElementById('login-modal');
            const registerModal = document.getElementById('register-modal');
            const closeLoginModal = document.getElementById('close-login-modal');
            const closeRegisterModal = document.getElementById('close-register-modal');
            const showRegisterFromLogin = document.getElementById('show-register-from-login');
            const showLoginFromRegister = document.getElementById('show-login-from-register');
            const searchInput = document.getElementById('search-input');
            const searchContainer = document.getElementById('search-container');
            const searchSuggestions = document.getElementById('search-suggestions');
            
                  
            // Función para mostrar un modal
            function showModal(modal) {
                modal.classList.remove('hidden');
                setTimeout(() => {
                    modal.querySelector('.modal').classList.add('active');
                }, 10);
            }
            
            // Función para ocultar un modal
            function hideModal(modal) {
                modal.querySelector('.modal').classList.remove('active');
                setTimeout(() => {
                    modal.classList.add('hidden');
                }, 300);
            }
            
            // Event listeners
            
            // Menú móvil
            //mobileMenuBtn.addEventListener('click', toggleMobileMenu);
            
            // Mostrar modal de inicio de sesión
            loginBtn.addEventListener('click', () => showModal(loginModal));
            
            // Mostrar modal de registro
            registerBtn.addEventListener('click', () => showModal(registerModal));
            
            // Cerrar modales
            closeLoginModal.addEventListener('click', () => hideModal(loginModal));
            closeRegisterModal.addEventListener('click', () => hideModal(registerModal));
            
            // Alternar entre modales de inicio de sesión y registro
            showRegisterFromLogin.addEventListener('click', (e) => {
                e.preventDefault();
                hideModal(loginModal);
                showModal(registerModal);
            });
            
            showLoginFromRegister.addEventListener('click', (e) => {
                e.preventDefault();
                hideModal(registerModal);
                showModal(loginModal);
            });
            
            // Cerrar modales al hacer clic fuera del contenido
            loginModal.addEventListener('click', (e) => {
                if (e.target === loginModal) {
                    hideModal(loginModal);
                }
            });
            
            registerModal.addEventListener('click', (e) => {
                if (e.target === registerModal) {
                    hideModal(registerModal);
                }
            });
            
            // Efectos de búsqueda
            searchInput.addEventListener('focus', () => {
                searchContainer.classList.add('focused');
                searchSuggestions.classList.remove('hidden');
            });
            
            searchInput.addEventListener('blur', () => {
                searchContainer.classList.remove('focused');
                // Ocultar sugerencias después de un pequeño retraso para permitir clics
                setTimeout(() => {
                    if (!searchInput.matches(':focus')) {
                        searchSuggestions.classList.add('hidden');
                    }
                }, 200);
            });
            
            // Manejar el envío de formularios
            document.getElementById('login-form').addEventListener('submit', (e) => {
                e.preventDefault();
                // Aquí iría la lógica para autenticar al usuario
                alert('Inicio de sesión simulado. En una implementación real, esto autenticaría al usuario.');
                hideModal(loginModal);
            });
            
            document.getElementById('register-form').addEventListener('submit', (e) => {
                e.preventDefault();
                // Aquí iría la lógica para registrar al usuario
                alert('Registro simulado. En una implementación real, esto registraría al usuario.');
                hideModal(registerModal);
            });
            
            // Simular datos de libros (en una aplicación real, esto vendría de una API)
            const books = [
                { title: "Introducción a la Programación", author: "John Doe", available: true },
                { title: "Historia del Arte Moderno", author: "Jane Smith", available: true },
                { title: "Matemáticas Avanzadas", author: "Robert Johnson", available: false },
                { title: "Física Cuántica", author: "María García", available: true }
            ];
            
            // Búsqueda en tiempo real (simulada)
            searchInput.addEventListener('input', () => {
                const query = searchInput.value.toLowerCase();
                if (query.length > 2) {
                    // Filtrar libros que coincidan con la consulta
                    const results = books.filter(book => 
                        book.title.toLowerCase().includes(query) || 
                        book.author.toLowerCase().includes(query)
                    );
                    
                    // Mostrar sugerencias (simplificado para este ejemplo)
                    if (results.length > 0) {
                        searchSuggestions.innerHTML = `
                            <div class="bg-white border border-gray-200 rounded shadow-lg p-2">
                                <p class="text-sm text-gray-500 px-2 py-1">Sugerencias:</p>
                                ${results.map(book => `
                                    <a href="#" class="block px-2 py-1 hover:bg-gray-100 rounded">${book.title} - ${book.author}</a>
                                `).join('')}
                            </div>
                        `;
                        searchSuggestions.classList.remove('hidden');
                    } else {
                        searchSuggestions.innerHTML = `
                            <div class="bg-white border border-gray-200 rounded shadow-lg p-2">
                                <p class="text-sm text-gray-500 px-2 py-1">No se encontraron resultados</p>
                            </div>
                        `;
                    }
                } else {
                    searchSuggestions.classList.add('hidden');
                }
            });
            
            // Manejar reservas de libros
            document.querySelectorAll('.book-card button:not(:disabled)').forEach(button => {
                button.addEventListener('click', function(e) {
                    e.preventDefault();
                    const card = this.closest('.book-card');
                    const title = card.querySelector('h3').textContent;
                    alert(`Has reservado el libro: ${title}`);
                });
            });
        });
    </script>
</body>
</html>
