<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda Virtual - Sábanas & Cortinas</title>
    <style>
        :root {
            /* PALETA ORIGINAL MANTENIDA */
            --bg-principal: #ffffff;      
            --bg-card: #f2efe7;           
            --texto: #333333;              
            --texto-secundario: #666666;   
            --detalles-muda: #8ba3b4;      
            --color-acento: #bd9b75;       
            --precio-verde: #2e7d32;       
            --banner-bg: #deca9b;          
            --sombras: rgba(0, 0, 0, 0.06); 
            
            /* ==========================================================================
               NUEVA PALETA DE DESCUENTOS LLAMATIVOS (NEÓN Y FUEGO)
               ========================================================================== */
            --rojo-descuento-neon: #ff1744; /* Rojo neón vibrante */
            --rojo-oscuro-deep: #b71c1c;   /* Rojo oscuro para gradiente */
            --amarillo-fuego: #ffea00;     /* Amarillo para destellos de fuego */
            
            /* Colores originales mantenidos para compatibilidad si fuesen necesarios */
            --rojo-descuento: #ff1744; 
            --rojo-oscuro: #b71c1c;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-principal);
            color: var(--texto);
            padding-bottom: 80px;
        }

        header {
            text-align: center;
            padding: 0px 0px;
            background: linear-gradient(180deg, #ffffff 0%, var(--bg-principal) 100%);
            border-bottom: 1px solid rgba(0, 0, 0, 0.05);
        }

        /* ==========================================================================
           MODIFICACIÓN Y NUEVOS ESTILOS DE DESCUENTO LLAMATIVOS Y CON ANIMACIONES
           ========================================================================== */
        
        /* 1. La Etiqueta (Badge) Flotante (MODIFICADO: Forma de Llama, Resplandor, Animación) */
        .badge-descuento {
            position: absolute;
            top: -15px; /* Más arriba para que sobresalga */
            left: -10px; /* Hacia la izquierda */
            
            /* Gradiente estilo fuego */
            background: linear-gradient(0deg, var(--rojo-oscuro-deep) 0%, var(--rojo-descuento-neon) 50%, var(--amarillo-fuego) 100%);
            color: white;
            padding: 10px 14px;
            font-size: 1rem;
            font-weight: 900;
            
            /* Forma de llama/púa */
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            z-index: 10; /* Asegurar que esté por encima de TODO */
            
            /* EFECTO DE RESPLANDOR (GLOW) DE NEÓN */
            box-shadow: 
                0 0 10px var(--rojo-descuento-neon),
                0 0 20px var(--rojo-descuento-neon),
                0 0 30px var(--amarillo-fuego);
                
            text-transform: uppercase;
            letter-spacing: 0.5px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 2px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5); /* Sombra de texto para legibilidad */
            
            /* Animaciones Combinadas: Entrada + Pulso Resplandor + Flotación */
            animation: 
                zoomInDescuento 0.5s ease-out both, 
                pulseNeonGlow 1.5s infinite alternate 0.6s,
                floatingFlame 3s ease-in-out infinite 0.6s;
            transform-origin: center center;
        }

        /* Icono de fuego dentro del badge con animación propia */
        .badge-descuento::before {
            content: '🔥';
            font-size: 1.1rem;
            animation: flickerFlame 0.3s infinite alternate;
        }

        /* 2. Precio Anterior (Tachado) */
        .precio-antes {
            font-size: 0.95rem;
            color: #888;
            text-decoration: line-through;
            text-decoration-color: var(--rojo-descuento-neon);
            margin-right: 10px;
            font-weight: normal;
        }

        /* 3. Texto de Alerta de Ahorro (Debajo del selector) (MODIFICADO: Resplandor sutil) */
        .alerta-ahorro {
            display: inline-block;
            font-size: 0.8rem;
            color: var(--rojo-descuento-neon);
            font-weight: bold;
            margin-bottom: 8px;
            background-color: rgba(255, 23, 68, 0.1); /* Fondo rojo muy suave */
            padding: 4px 10px;
            border-radius: 20px; /* Bordes más redondeados */
            transition: all 0.3s ease;
            
            /* EFECTO DE RESPLANDOR (GLOW) SUTIL */
            box-shadow: 0 0 8px rgba(255, 23, 68, 0.4);
            border: 1px solid rgba(255, 23, 68, 0.2);
            
            /* Animación de pulso de texto */
            animation: pulseTextGlow 2s infinite alternate;
        }
        
        /* Efecto cuando cambia el precio al seleccionar medida (NUEVO: Glow al actualizar) */
        .precio-actualizado {
            animation: highlightUpdateGlow 0.6s ease;
            position: relative;
        }

        /* 4. Resaltado de descuento en el MODAL (MODIFICADO: Neón intenso y borde animado) */
        .contenedor-precio-modal-descuento {
            background-color: #0c0000; /* Fondo casi negro para resaltar el neón */
            
            /* Borde de Neón */
            border: 3px solid var(--rojo-descuento-neon);
            padding: 18px;
            border-radius: 12px;
            margin: 20px 0;
            position: relative;
            
            /* EFECTO DE RESPLANDOR (GLOW) INTENSO */
            box-shadow: 
                0 0 15px var(--rojo-descuento-neon),
                inset 0 0 15px rgba(255, 23, 68, 0.5);
                
            /* Animación del borde */
            animation: borderPulseNeon 2s infinite alternate;
        }

        .tag-modal-descuento {
            position: absolute;
            top: -14px;
            right: 20px;
            background: linear-gradient(90deg, var(--rojo-descuento-neon) 0%, var(--rojo-oscuro-deep) 100%);
            color: white;
            padding: 3px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            
            /* Resplandor del tag */
            box-shadow: 0 0 10px var(--rojo-descuento-neon);
        }

        /* Clase especial para la tarjeta que tiene descuento */
        .producto-card.tiene-descuento {
            border: 2px solid rgba(255, 23, 68, 0.3);
            /* Un resplandor muy suave alrededor de toda la tarjeta */
            box-shadow: 0 4px 12px var(--sombras), 0 0 10px rgba(255, 23, 68, 0.15);
        }

        /* ==========================================================================
           DEFINICIÓN DE NUEVAS ANIMACIONES (KEYFRAMES)
           ========================================================================== */
        
        /* Animación de entrada suave con zoom */
        @keyframes zoomInDescuento {
            from { opacity: 0; transform: scale(0.5) translateY(-20px) rotate(-15deg); }
            to { opacity: 1; transform: scale(1) translateY(0) rotate(0deg); }
        }

        /* Animación de pulso de Resplandor Neón (Badge) */
        @keyframes pulseNeonGlow {
            0% { 
                box-shadow: 
                    0 0 5px var(--rojo-descuento-neon),
                    0 0 10px var(--rojo-descuento-neon),
                    0 0 15px var(--amarillo-fuego);
            }
            100% { 
                box-shadow: 
                    0 0 15px var(--rojo-descuento-neon),
                    0 0 30px var(--rojo-descuento-neon),
                    0 0 50px var(--amarillo-fuego);
            }
        }
        
        /* Animación de flotación suave (Badge) */
        @keyframes floatingFlame {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-5px) rotate(3deg); }
        }
        
        /* Parpadeo del icono de fuego */
        @keyframes flickerFlame {
            0% { opacity: 0.8; transform: scale(0.9); }
            100% { opacity: 1; transform: scale(1.1); }
        }

        /* Pulso del texto de ahorro */
        @keyframes pulseTextGlow {
            0% { text-shadow: 0 0 2px rgba(255, 23, 68, 0.3); box-shadow: 0 0 5px rgba(255, 23, 68, 0.2); }
            100% { text-shadow: 0 0 8px rgba(255, 23, 68, 0.7); box-shadow: 0 0 12px rgba(255, 23, 68, 0.5); }
        }
        
        /* Flash de Glow Neón al actualizar precio */
        @keyframes highlightUpdateGlow {
            0% { 
                color: #ffffff;
                text-shadow: 0 0 10px #ffffff, 0 0 20px var(--precio-verde);
                transform: scale(1.1);
            }
            100% { 
                color: var(--precio-verde);
                text-shadow: none;
                transform: scale(1);
            }
        }
        
        /* Pulso del borde Neón en el Modal */
        @keyframes borderPulseNeon {
            0% { 
                border-color: rgba(255, 23, 68, 0.6);
                box-shadow: 0 0 10px rgba(255, 23, 68, 0.4), inset 0 0 10px rgba(255, 23, 68, 0.3);
            }
            100% { 
                border-color: rgba(255, 23, 68, 1);
                box-shadow: 0 0 25px rgba(255, 23, 68, 0.8), inset 0 0 20px rgba(255, 23, 68, 0.6);
            }
        }

        /* ==========================================================================
           Resto de estilos originales mantenidos...
           ========================================================================== */
        header h1 {
            font-size: 1.8rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #333333;
        }

     /* ==========================================================================
           LETRERO CRONOGRAMA: OPTIMIZADO PASO A PASO Y SÚPER CLARO
           ========================================================================== */
        .banner-pedidos {
            background: linear-gradient(135deg, #fdfbf7 0%, #eae5d9 100%);
            margin: 20px 15px;
            padding: 22px 15px;
            text-align: center;
            position: relative;
            border-radius: 16px;
            box-shadow: 0 8px 24px rgba(189, 155, 117, 0.2);
            border: 2px solid var(--color-acento);
            overflow: hidden;
            z-index: 1;
            animation: pulsoInicial 1.5s ease-in-out infinite alternate;
        }

        .banner-pedidos::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 5px;
            background: linear-gradient(90deg, var(--color-acento), #4a7c59);
        }

        .banner-pedidos::after {
            content: '';
            position: absolute;
            top: 0; left: -150%; width: 50%; height: 100%;
            background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.6) 50%, rgba(255,255,255,0) 100%);
            transform: skewX(-20deg);
            z-index: 2;
            animation: brilloContinuo 6s infinite linear;
        }

        .banner-pedidos h2 {
            color: #4a3b32;
            font-size: 1.25rem;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 1px;
            text-shadow: 1px 1px 0px rgba(255,255,255,0.8);
        }

        .cronograma-pasos {
            display: flex;
            flex-direction: column;
            gap: 12px;
            text-align: left;
            max-width: 360px;
            margin: 0 auto;
        }

        .paso-item {
            display: flex;
            align-items: center;
            gap: 12px;
            background: rgba(255, 255, 255, 0.6);
            padding: 10px 12px;
            border-radius: 10px;
            border: 1px solid rgba(0, 0, 0, 0.03);
        }

        .paso-numero {
            background-color: var(--color-acento);
            color: white;
            font-weight: bold;
            font-size: 0.9rem;
            width: 26px;
            height: 26px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }

        .paso-item.resaltado .paso-numero {
            background-color: #2e7d32;
            animation: tildePulso 1s infinite alternate;
        }

        .paso-texto {
            font-size: 0.9rem;
            line-height: 1.4;
            color: #333;
        }

        .paso-texto strong {
            color: #111;
            font-weight: 700;
        }
        
        .paso-texto .alerta-roja {
            color: #c62828;
            font-weight: 700;
        }

        .contenedor-busqueda {
            margin: 0 60px 0.1px 60px;
            position: relative;
        }

        .input-busqueda {
            width: 100%;
            padding: 12px 16px 12px 40px;
            font-size: 0.8rem;
            border-radius: 30px;
            border: 1px solid rgba(0,0,0,0.12);
            background-color: var(--bg-card);
            color: var(--texto);
            outline: none;
            box-shadow: 0 3px 8px var(--sombras);
            transition: all 0.3s ease;
        }

        .input-busqueda:focus {
            border-color: var(--color-acento);
            box-shadow: 0 4px 12px rgba(189, 155, 117, 0.2);
        }

        .icono-busqueda {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--texto-secundario);
            font-size: 1.1rem;
            pointer-events: none;
        }

        @keyframes pulsoInicial {
            0% { transform: scale(1); box-shadow: 0 8px 24px rgba(189, 155, 117, 0.2); }
            100% { transform: scale(1.01); box-shadow: 0 12px 30px rgba(189, 155, 117, 0.3); border-color: #4a7c59; }
        }

        @keyframes brilloContinuo {
            0% { left: -150%; }
            30% { left: 150%; }
            100% { left: 150%; }
        }

        @keyframes tildePulso {
            0% { transform: scale(1); }
            100% { transform: scale(1.1); }
        }

       .nav-categorias {
            display: flex;
            justify(135deg, #fdfbf7 0%, #eae5d9 100%);
            margin: 20px 15px;
            padding: 22px 15px;
            text-align: center;
            position: relative;
            border-radius: 16px;
            box-shadow: 0 8px 24px rgba(189, 155, 117, 0.2);
            border: 2px solid var(--color-acento);
            overflow: hidden;
            z-index: 1;
            animation: pulsoInicial 1.5s ease-in-out infinite alternate;
        }

        .banner-pedidos::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 5px;
            background: linear-gradient(90deg, var(--color-acento), #4a7c59);
        }

        .banner-pedidos::after {
            content: '';
            position: absolute;
            top: 0; left: -150%; width: 50%; height: 100%;
            background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.6) 50%, rgba(255,255,255,0) 100%);
            transform: skewX(-20deg);
            z-index: 2;
            animation: brilloContinuo 6s infinite linear;
        }

        .banner-pedidos h2 {
            color: #4a3b32;
            font-size: 1.25rem;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 1px;
            text-shadow: 1px 1px 0px rgba(255,255,255,0.8);
        }

        .cronograma-pasos {
            display: flex;
            flex-direction: column;
            gap: 12px;
            text-align: left;
            max-width: 360px;
            margin: 0 auto;
        }

        .paso-item {
            display: flex;
            align-items: center;
            gap: 12px;
            background: rgba(255, 255, 255, 0.6);
            padding: 10px 12px;
            border-radius: 10px;
            border: 1px solid rgba(0, 0, 0, 0.03);
        }

        .paso-numero {
            background-color: var(--color-acento);
            color: white;
            font-weight: bold;
            font-size: 0.9rem;
            width: 26px;
            height: 26px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }

        .paso-item.resaltado .paso-numero {
            background-color: #2e7d32;
            animation: tildePulso 1s infinite alternate;
        }

        .paso-texto {
            font-size: 0.9rem;
            line-height: 1.4;
            color: #333;
        }

        .paso-texto strong {
            color: #111;
            font-weight: 700;
        }
        
        .paso-texto .alerta-roja {
            color: #c62828;
            font-weight: 700;
        }

        .contenedor-busqueda {
            margin: 0 60px 0.1px 60px;
            position: relative;
        }

        .input-busqueda {
            width: 100%;
            padding: 12px 16px 12px 40px;
            font-size: 0.8rem;
            border-radius: 30px;
            border: 1px solid rgba(0,0,0,0.12);
            background-color: var(--bg-card);
            color: var(--texto);
            outline: none;
            box-shadow: 0 3px 8px var(--sombras);
            transition: all 0.3s ease;
        }

        .input-busqueda:focus {
            border-color: var(--color-acento);
            box-shadow: 0 4px 12px rgba(189, 155, 117, 0.2);
        }

        .icono-busqueda {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--texto-secundario);
            font-size: 1.1rem;
            pointer-events: none;
        }

        @keyframes pulsoInicial {
            0% { transform: scale(1); box-shadow: 0 8px 24px rgba(189, 155, 117, 0.2); }
            100% { transform: scale(1.01); box-shadow: 0 12px 30px rgba(189, 155, 117, 0.3); border-color: #4a7c59; }
        }

        @keyframes brilloContinuo {
            0% { left: -150%; }
            30% { left: 150%; }
            100% { left: 150%; }
        }

        @keyframes tildePulso {
            0% { transform: scale(1); }
            100% { transform: scale(1.1); }
        }

       .nav-categorias {
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow-x: auto;
            white-space: nowrap;
            padding: 10px 10px;
            gap: 10px;
            scrollbar-width: none;
            -webkit-overflow-scrolling: touch; 
        }

        .nav-categorias::-webkit-scrollbar {
            display: none;
        }
   
        .subcategorias-container {
            padding: 0 15px 5px 5px;
            width: 100%;
            display: flex;
            justify-content: center;
        }

        .subcat-wrapper {
            display: none;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
            padding-bottom: 10px;
            width: 100%;
            max-width: 100%;
        }

        .subcat-wrapper.activo {
            display: flex;
        }

        .catalogo {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
            gap: 20px;
            padding: 15px;
        }

        .producto-card {
            background-color: var(--bg-card);
            border-radius: 12px;
            overflow: visible; /* Cambiado de hidden para permitir que el badge sobresalga */
            border: 1px solid rgba(0,0,0,0.04);
            display: flex;
            flex-direction: column;
            transition: transform 0.3s cubic-bezier(0.25, 0.8, 0.25, 1), box-shadow 0.3s ease;
            box-shadow: 0 4px 12px var(--sombras);
            animation: aparecerCard 0.9s ease-out both;
            position: relative;
        }

        @keyframes abrir-modal {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes aparecerCard {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .producto-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
        }

        .producto-img-contenedor {  
            width: 100%;
            height: 240px;
            overflow: hidden;
            background-color: #f0f0f0;
            position: relative;
            z-index: 1;
            border-radius: 12px 12px 0 0; /* Mantener bordes redondeados arriba */
        }

        .producto-img-contenedor::after {
            content: '';
            position: absolute;
            top: 0; left: -150%; width: 50%; height: 100%;
            background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.6) 50%, rgba(255,255,255,0) 100%);
            transform: skewX(-20deg);
            z-index: 2;
            pointer-events: none;
            animation: brilloContinuo 6s infinite linear;
        }

        .producto-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            cursor: pointer;
            transition: transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        .producto-card:hover .producto-img {
            transform: scale(1.08);
        }

        .producto-info {
            padding: 14px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
            background-color: var(--bg-card);
            border-radius: 0 0 12px 12px;
            z-index: 2; /* Asegurar que está sobre el brillo de la imagen */
        }

        .producto-ref {
            font-size: 0.75rem;
            color: var(--detalles-muda);
            font-weight: bold;
            margin-bottom: 4px;
        }

        .producto-titulo {
            font-size: 1rem;
            font-weight: 600;
            color: #2c3e50;
            margin-bottom: 8px;
            line-height: 1.3;
            height: 2.6rem;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            cursor: pointer;
        }

        .select-medida {
            width: 100%;
            background-color: #fdfdfd;
            color: #333;
            border: 1px solid rgba(0,0,0,0.15);
            padding: 8px;
            border-radius: 6px;
            font-size: 0.85rem;
            margin-bottom: 12px;
            outline: none;
        }

        .select-medida:focus {
            border-color: var(--color-acento);
        }

        .producto-precio {
            font-size: 1.35rem;
            font-weight: 800;
            color: var(--precio-verde);
            margin-top: auto;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            flex-wrap: wrap;
        }

        .btn-cat {
            background-color: var(--bg-card);
            color: var(--texto-secundario);
            border: 1px solid rgba(0, 0, 0, 0.08);
            padding: 9px 9px;
            font-size: 0.8rem;
            font-weight: 600;
            border-radius: 25px;
            cursor: pointer;
            box-shadow: 0 2px 5px var(--sombras);
            transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
            display: inline-flex;
            align-items: center;
            gap: 6px;
        }

        .btn-cat:hover {
            transform: translateY(-2px);
            background-color: #ffffff;
            border-color: var(--color-acento);
            color: var(--texto);
            box-shadow: 0 5px 12px rgba(189, 155, 117, 0.25);
        }

        .btn-cat.activo {
            background: linear-gradient(135deg, #4a3b32 0%, #2c211a 100%);
            color: #ffffff;
            border-color: transparent;
            box-shadow: 0 4px 10px rgba(74, 59, 50, 0.3);
        }

        .btn-subcat {
            background: transparent;
            color: var(--texto-secundario);
            border: none;
            padding: 6px 12px;
            font-size: 0.9rem;
            font-weight: 500;
            cursor: pointer;
            position: relative;
            transition: color 0.3s ease;
        }

        .btn-subcat:hover { color: var(--texto); }

        .btn-subcat::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 2px;
            background-color: var(--color-acento);
            transition: all 0.3s ease;
            transform: translateX(-50%);
        }

        .btn-subcat.activo {
            color: var(--texto);
            font-weight: 700;
        }

        .btn-subcat.activo::after, 
        .btn-subcat:hover::after {
            width: 80%;
        }

        .btn-agregar {
            width: 100%;
            background: linear-gradient(90deg, #4a7c59, #68b0ab);
            color: #fff;
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-weight: bold;
            font-size: 0.95rem;
            cursor: pointer;
            box-shadow: 0 3px 8px rgba(74, 124, 89, 0.25);
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            z-index: 1;
        }

        .btn-agregar:hover {
            box-shadow: 0 5px 15px rgba(74, 124, 89, 0.4);
            transform: translateY(-1px);
        }

        .btn-ver-pedido {
            background: linear-gradient(135deg, var(--color-acento) 0%, #a4825b 100%);
            color: #fff;
            border: none;
            padding: 12px 24px;
            border-radius: 30px;
            font-weight: bold;
            font-size: 0.95rem;
            letter-spacing: 0.5px;
            box-shadow: 0 4px 12px rgba(189, 155, 117, 0.4);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .modal-contenido {
            background-color: var(--bg-card);
            border: 1px solid rgba(0,0,0,0.1);
            border-radius: 16px;
            width: 100%;
            max-width: 440px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
            animation: abrir-modal 0.3s ease-out;
        }

        .btn-cerrar {
            position: absolute;
            top: 12px; right: 12px;
            background: rgba(0,0,0,0.4);
            color: #fff;
            border: none;
            width: 30px; height: 30px;
            border-radius: 50%;
            font-size: 1.2rem;
            font-weight: bold;
            z-index: 10;
            cursor: pointer;
        }

        .modal-img-contenedor {
            width: 100%;
            height: 320px;
            overflow: hidden;
            position: relative;
            z-index: 1;
            background-color: #f0f0f0;
        }

        .modal-img-contenedor::after {
            content: '';
            position: absolute;
            top: 0; left: -150%; width: 50%; height: 100%;
            background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.6) 50%, rgba(255,255,255,0) 100%);
            transform: skewX(-20deg);
            z-index: 2;
            pointer-events: none;
            animation: brilloContinuo 6s infinite linear;
        }

        .modal-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }

        .modal-detalles { padding: 20px; }
        .modal-desc { font-size: 0.9rem; color: var(--texto-secundario); margin: 10px 0 15px 0; line-height: 1.4; }

        .barra-carrito {
            position: fixed;
            bottom: 0; left: 0; width: 100%;
            background-color: #ffffff;
            border-top: 1px solid rgba(0,0,0,0.08);
            padding: 12px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 900;
            box-shadow: 0 -4px 15px var(--sombras);
        }

        .carrito-info h3 { font-size: 0.85rem; color: var(--texto-secundario); }
        .carrito-total { font-size: 1.3rem; font-weight: bold; color: var(--precio-verde); }

        .checkout-items {
            max-height: 200px;
            overflow-y: auto;
            margin-bottom: 15px;
            border-bottom: 1px solid rgba(0,0,0,0.08);
            padding-bottom: 10px;
        }

        .checkout-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.9rem;
            margin-bottom: 8px;
            background: rgba(0, 0, 0, 0.02);
            padding: 8px;
            border-radius: 6px;
            color: #333;
        }

        .checkout-item-info { display: flex; flex-direction: column; max-width: 70%; }
        .checkout-item-acciones { display: flex; align-items: center; gap: 10px; }

        .btn-eliminar {
            background-color: rgba(211, 47, 47, 0.1);
            color: #d32f2f;
            border: 1px solid #d32f2f;
            width: 26px;
            height: 26px;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .grupo-formulario { margin-top: 12px; margin-bottom: 12px; }
        .grupo-formulario label { display: block; margin-bottom: 6px; font-size: 0.9rem; font-weight: bold; color: #4a3b32; }

        .input-formulario {
            width: 100%;
            background-color: #fdfdfd;
            color: #333;
            border: 1px solid rgba(0,0,0,0.15);
            padding: 10px;
            border-radius: 6px;
            font-size: 0.9rem;
            outline: none;
        }

        .select-pago {
            width: 100%;
            background-color: #fdfdfd;
            color: #333;
            border: 1px solid rgba(0,0,0,0.15);
            padding: 10px;
            border-radius: 6px;
            font-size: 0.9rem;
            margin-bottom: 15px;
        }

        .info-transferencia {
            display: none;
            background: rgba(139, 163, 180, 0.08);
            border: 1px dashed var(--detalles-muda);
            padding: 12px;
            border-radius: 6px;
            font-size: 0.85rem;
            margin-bottom: 15px;
            line-height: 1.5;
            color: #444;
        }

        footer {
            text-align: center;
            padding: 25px;
            font-size: 0.8rem;
            color: var(--texto-secundario);
            border-top: 1px solid rgba(0,0,0,0.05);
            margin-top: 30px;
        }

        footer strong { color: var(--color-acento); }

        .btn-enviar-wa {
            width: 100%;
            background: linear-gradient(135deg, #25D366 0%, #128C7E 100%);
            color: #fff;
            border: none;
            padding: 14px;
            border-radius: 8px;
            font-weight: bold;
            font-size: 1.05rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            margin-top: 20px;
            box-shadow: 0 4px 15px rgba(37, 211, 102, 0.2);
        }

        .btn-enviar-wa vsg { width: 22px; height: 22px; fill: currentColor; }

        .contenedor-logo { max-width: 200px; width: 100%; margin: 0 auto; display: block; }
        .logo-img { width: 100%; height: auto; object-fit: contain; display: block; }

        .seccion-atencion {
            background-color: var(--bg-card);
            margin: 20px 15px;
            padding: 20px;
            border-radius: 12px;
            border: 1px solid rgba(0,0,0,0.05);
            box-shadow: 0 4px 12px var(--sombras);
            text-align: center;
            
            /* EFECTO DE ANIMACIÓN Y RESPLANDOR (GLOW) */
            border: 1px solid rgba(189, 155, 117, 0.3); /* Borde suave de acento */
            box-shadow: 0 0 15px rgba(189, 155, 117, 0.3), 0 4px 12px var(--sombras);
            animation: pulsateGlow 2.5s infinite ease-in-out alternate;
        }

        .seccion-atencion h2 { font-size: 1.2rem; color: #4a3b32; margin-bottom: 15px; text-transform: uppercase; }

        .grid-atencion { display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 12px; margin-top: 10px; }

        .tarjeta-atencion {
            background-color: #ffffff;
            padding: 15px 10px;
            border-radius: 8px;
            border: 1px solid rgba(0, 0, 0, 0.03);
            text-decoration: none;
            color: var(--texto);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            transition: all 0.3s ease;
        }
        
        .tarjeta-atencion:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 18px rgba(0,0,0,0.1);
            border-color: rgba(189, 155, 117, 0.5);
        }

        .tarjeta-atencion span {
            font-size: 2rem;
            animation: iconWiggle 3s infinite ease-in-out alternate;
        }
        
        /* ==========================================================================
           DEFINICIÓN DE NUEVAS ANIMACIONES PARA ATENCIÓN AL CLIENTE (KEYFRAMES)
           ========================================================================= */
           
        /* Pulso de Resplandor sutil para la sesión */
        @keyframes pulsateGlow {
            0% { box-shadow: 0 0 15px rgba(189, 155, 117, 0.3), 0 4px 12px var(--sombras); }
            100% { box-shadow: 0 0 25px rgba(189, 155, 117, 0.6), 0 6px 15px rgba(0,0,0,0.1); }
        }

        /* Movimiento de vaivén suave para los iconos */
        @keyframes iconWiggle {
            0%, 100% { transform: rotate(-5deg) scale(1); }
            50% { transform: rotate(5deg) scale(1.1); }
        }
    </style>
</head>
<body>

  <header>
    <div class="contenedor-logo">
        <img src="https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/721110501_887045387746120_3221405514702502319_n.jpg?stp=dst-jpg_tt6&cstp=mx2048x2048&ctp=s2048x2048&_nc_cat=104&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeEu3YPVVz1-Jl35T9mjmxkEOwUTHbFJ4m87BRMdsUnibzBhLHtwBAHea2my3ulOov-vm0uLCWoFshZAR4DpoUmL&_nc_ohc=tbt5fIZG7WYQ7kNvwG1fRD7&_nc_oc=AdqYP25-mxhwqmX91l1XzXHf-gLl-bVTxU0pcxnonFyp2q0rhxCpqkj_eDMqfSweeQA&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=8uMHaJAy_Bw1L6wEaPCPNg&_nc_ss=7b2a8&oh=00_Af9zRG_x1JcISZiUL59XZtHsRqrwdsIwl8TL3lVN46pycQ&oe=6A317083" alt="Dulces Sueños - Hogar, Sábanas & Cortinas" class="logo-img">
    </div>
</header>

    <div class="banner-pedidos">
        <h2>¿Cómo funciona tu pedido?</h2>
        <div id="mensaje-fomo" class="cronograma-pasos"></div>
    </div>

    <div class="contenedor-busqueda">
        <span class="icono-busqueda">🔍</span>
        <input type="text" id="input-filtrar" class="input-busqueda" placeholder="Buscar producto por nombre, ref o diseño..." oninput="ejecutarBusquedaCompleta()">
    </div>

    <nav class="nav-categorias">
        <button class="btn-cat activo" onclick="cambiarCategoria('sabanas', this)"> Sábanas </button>
        <button class="btn-cat" onclick="cambiarCategoria('acolchados', this)">Acolchados</button>
        <button class="btn-cat" onclick="cambiarCategoria('cortinas', this)">Cortinas</button>
        <button class="btn-cat" onclick="cambiarCategoria('sabanas_exclusivas', this)">Protector</button>
    </nav>

    <div class="subcategorias-container">
       <div id="sub-sabanas" class="subcat-wrapper activo">
            <button class="btn-subcat activo" onclick="filtrarSubcategoria('matrimonial', this)">Matrimonial</button>
            <button class="btn-subcat" onclick="filtrarSubcategoria('unicolor', this)">Unicolor</button>
            <button class="btn-subcat" onclick="filtrarSubcategoria('infantil-nino', this)">Infantil</button>
            <button class="btn-subcat" onclick="filtrarSubcategoria('sale', this)" style="color: #ff1744; font-weight: bold; text-shadow: 0 0 5px rgba(255,23,68,0.5);">🔥Sale</button>
        </div>
        
        <div id="sub-acolchados" class="subcat-wrapper">
            <button class="btn-subcat" onclick="filtrarSubcategoria('colcha-espanola', this)">Colcha Española</button>
        </div>

        <div id="sub-cortinas" class="subcat-wrapper">
            <button class="btn-subcat activo" onclick="filtrarSubcategoria('clasica', this)">Exclusiva / Clásica</button>
            <button class="btn-subcat" onclick="filtrarSubcategoria('infantiles', this)">Infantiles</button>
        </div>
    </div>
    <div id="sub-sabanas_exclusivas" class="subcat-wrapper">
        <button class="btn-subcat activo" onclick="filtrarSubcategoria('200-hilos', this)">Protector impermeable</button>
    </div>
        <div id="sub-protector" class="subcat-wrapper">
            <button class="btn-subcat activo" onclick="filtrarSubcategoria('impermeable', this)">Protector Impermeable</button>
        </div>
    <main class="catalogo" id="contenedor-productos"></main>

    <div class="modal" id="modal-detail">
        <div class="modal-contenido">
            <button class="btn-cerrar" onclick="cerrarModal('modal-detail')">&times;</button>
            <div class="modal-img-contenedor">
                <img id="det-img" src="" alt="" class="modal-img">
            </div>
            <div class="modal-detalles">
                <span id="det-ref" class="producto-ref"></span>
                <h2 id="det-titulo" style="font-size:1.3rem; margin: 5px 0; color: #2c3e50;"></h2>
                
                <div style="margin: 10px 0;">
                    <label style="font-size:0.85rem; color: var(--color-acento); font-weight:bold; display:block; margin-bottom:4px;">Selecciona la Medida:</label>
                    <select id="det-select-medida" class="select-medida" style="margin-bottom:0;" onchange="actualizarPrecioModal()"></select>
                </div>

                <!-- Contenedor de precio modificado dinámicamente en JS para descuentos -->
                <div id="det-contenedor-precio">
                    <div id="det-precio" class="producto-precio" style="margin-top:10px;"></div>
                </div>
                
                <p id="det-desc" class="modal-desc"></p>
                <button id="det-btn-agregar" class="btn-agregar" style="padding:12px; font-size:1rem;">Agregar al Pedido</button>
            </div>
        </div>
    </div>

    <div class="modal" id="modal-checkout">
        <div class="modal-contenido" style="padding: 20px;">
            <button class="btn-cerrar" onclick="cerrarModal('modal-checkout')">&times;</button>
            <h2 style="margin-bottom: 15px; color: #4a3b32;">Resumen de Pedido</h2>
            
            <div class="checkout-items" id="checkout-items"></div>
            
            <div style="display:flex; justify-content:space-between; font-weight:bold; margin-bottom:15px;">
                <span>Total a pagar:</span>
                <span id="checkout-total" style="color:var(--precio-verde);"></span>
            </div>

            <div class="grupo-formulario">
                <label for="cliente-nombre">Tu Nombre:</label>
                <input type="text" id="cliente-nombre" class="input-formulario" placeholder="Ej. María Pérez">
            </div>

            <div class="grupo-formulario">
                <label for="cliente-direccion">Dirección de Entrega / Barrio:</label>
                <input type="text" id="cliente-direccion" class="input-formulario" placeholder="Ej. Calle 10 #23-45 Barrio Centro">
            </div>

            <div class="grupo-formulario">
                <label for="cliente-telefono">Número de Teléfono / WhatsApp:</label>
                <input type="tel" id="cliente-telefono" class="input-formulario" placeholder="Ej. 3123456789">
            </div>

            <div class="grupo-formulario" style="margin-top: 15px;">
                <label for="pago-select">Forma de Pago:</label>
                <select id="pago-select" class="select-pago" onchange="controlarMetodoPago(this.value)">
                    <option value="Efectivo">En Efectivo</option>
                    <option value="Transferencia">Transferencia Bancaria (100% Anticipado)</option>
                </select>
            </div>

            <div id="info-banco" class="info-transferencia">
                <strong>Datos de Transferencia:</strong><br>
                Davivienda Ahorros: Nro. 4884 - 5534 - 3936<br>
                Bancolombia Ahorros: Nro. 454 - 612794 - 34<br>
                Nequi: 3128411473<br><br>
                *Envía el comprobante por WhatsApp al finalizar.
            </div>

            <button class="btn-enviar-wa" onclick="procesarCompra()">
                Confirmar Pedido por WhatsApp
            </button>
        </div>
    </div>

    <div class="barra-carrito">
        <div class="carrito-info">
            <h3 id="carrito-cant">0 Productos</h3>
            <div class="carrito-total" id="carrito-total">$0</div>
        </div>
        <button class="btn-ver-pedido" onclick="abrirCheckout()">Ver Pedido</button>
    </div>

    <section class="seccion-atencion">
        <h2>Atención al Cliente</h2>
        <div class="grid-atencion">
            <a href="https://api.whatsapp.com/send?phone=573189882787&text=Hola,%20tengo%20una%20duda%20sobre%20el%20catálogo" target="_blank" class="tarjeta-atencion">
                <span>💬</span>
                <p>Chat de WhatsApp</p>
                <small>Respuesta Inmediata</small>
            </a>
            <a href="tel:+573189882787" class="tarjeta-atencion">
                <span>📞</span>
                <p>Línea Directa</p>
                <small>Llamar Ahora</small>
            </a>
        </div>
    </section>

    <footer>
        <p>&copy; 2026 - Todos Los Derechos Están Reservados Para El Desarrollador: <strong>Sergio Chala</strong></p>
    </footer>

    <script>
        // MISMAS OPCIONES DE MEDIDAS MANTENIDAS
        const opcionesMedidas = {
            sabanas: [
                { nombre: "1.20 Semidoble", precio: 95000 },
                { nombre: "1.40 Doble", precio: 95000 },
                { nombre: "1.60 Queen", precio: 110000 },
                { nombre: "2x2 King", precio: 120000 }
            ],
            sabanas_exclusivas: [
                { nombre: "1.20 Semidoble", precio: 110000 },
                { nombre: "1.40 Doble", precio: 120000 },
                { nombre: "2x2 King", precio: 130000 }
            ],
            cortinas: [
                { nombre: "2 Paños (2.30 x 1.85 cm)", precio: 110000 }
            ],
            acolchados: [
                { nombre: "200 x 240 Sencilla", precio: 140000 },
                { nombre: "220 x 240 Doble", precio: 150000 },
                { nombre: "240 x 240 Queen", precio: 160000  },
                { nombre: "270 x 240 King", precio: 170000 }
            ],
            protector: [
                { nombre: "1.20 Semidoble", precio: 110000 },
                { nombre: "1.40 Doble", precio: 120000 },
                { nombre: "2x2 King", precio: 130000 }
            ]
        };

        // MISMOS PRODUCTOS MANTENIDOS
        const productos = [
            { id: 5001, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-01', titulo: 'SÁBANA VITA PRINT (LIQUIDACIÓN)', desc: '¡Descuento especial esta semana! Juego de sábanas estampado en calidad microfibra texturizada, 100% garantizadas.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/720057820_886199141164078_7754503143384965476_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=110&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeFgTWamKcnMyCE-ejaW1uEdqjmx76LA1nSqObHvosDWdFVNY_HDhFP_yLeC2nL0HfGAUosAXCdgqKmGHGjM61EQ&_nc_ohc=w0ZSINiwuksQ7kNvwGK3eX8&_nc_oc=AdrInrJzPJiJDWa3UB-77BN-vNkyTIpwDyu3ATYcBLnUvVw6EkY9CUDXpsgg7sWcs6s&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=m4jK96VNgS2ZputHY7Bk1g&_nc_ss=7b2a8&oh=00_Af_1xtQ0bUsGrX05NaW-vM4cLbgh2QSEgw-Zi9kqGIn-_g&oe=6A30C6F9', descuento: 15 },
            { id: 5002, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-02', titulo: 'SÁBANA COPENHAGUE (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/720138925_886199134497412_4462312343662174109_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=101&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeFYPpE4dxU-egFDhcv5U4yyh8JcSkjSSz-HwlxKSNJLP7AuXMyLhhY0TWUhG1OP4yNsVqWWoLf_EA6Li1wbbw_a&_nc_ohc=IY9N0QOMRvgQ7kNvwGGvm5K&_nc_oc=AdpzzP3qwGKcBpqrIis6kpU2hvhFWAa9L-839LZNyAHJLxnTUGgil2bihYQR4ewItU0&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=1d1q7alF7hBF3Z7kCwuhIA&_nc_ss=7b2a8&oh=00_Af_KwT3Y7yzUqqCRbYnhglJiL1z094jaINMSeO59JblXkA&oe=6A30A47B', descuento: 15 },
            { id: 5003, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-03', titulo: 'SÁBANA ALMA TEXTURA (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/722430870_886199137830745_9222888446806693847_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=110&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeFM6sbfd0MSvJcHbq2F2uD8uPnzYesRcW-4-fNh6xFxb21llHoaVUu-j8bT_yHrhIHCaU7kL5nRh-w-1D_VCQAe&_nc_ohc=laqDXsEaVk8Q7kNvwHCmtaa&_nc_oc=AdpDNP87SbEpa1hRGz_fUjIVczAZptKnijYCMiPbv6V97tu_VasCQ4EI2j4AjqgxP-g&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=EJojeeG4v7_r-YriXvHw3A&_nc_ss=7b2a8&oh=00_Af8_zqk7YPBXoO01942EYrfdQSVlqvNTRd5Mvl_i_WQz-Q&oe=6A30A99F', descuento: 15 },
            { id: 5004, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-04', titulo: 'SÁBANA MICRO COLOR (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/719506701_886199187830740_7982583377469336108_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=109&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeFcGAVXyHUr36R_wzo8vTWNjOf6AMq2MMmM5_oAyrYwyRJQAjH9prQnb2fwl4lLiNcNB2EaPck6kkn_2aq3YsJ1&_nc_ohc=Zf3hgXhvaAQQ7kNvwEFdyDA&_nc_oc=Adqu-_RzYV1OaHDKVZ43NHxu2VFh9pMpjtinyD030qDTcsSNZhCgzjnGNe1cIveiWhY&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=EJojeeG4v7_r-YriXvHw3A&_nc_ss=7b2a8&oh=00_Af9B317kWnuWYsdWKjza2WJQA_BG_9xTaItqg6PTm97i8Q&oe=6A30B03D', descuento: 15 },
            { id: 5005, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-05', titulo: 'SÁBANA NUBE GRÁFICA (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/723015366_886199191164073_2088933674840312392_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=101&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeFUJ2gpyqDaAImW0pQJ81mAl7wyBlfvFfCXvDIGV-8V8J3rSc_PeP4QvGqHe62W7nNl1L81cht2ep455FzwCvO3&_nc_ohc=foY2AULEv0MQ7kNvwGOfjnU&_nc_oc=AdpFu55CX2emERC2n8gCskdsp9F5rSIje6U9E_Vtmlfs9xra1q5O26_sXjR-5RRkdyw&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=EJojeeG4v7_r-YriXvHw3A&_nc_ss=7b2a8&oh=00_Af_UilUE5SrrW50kZbAA2QZI5WL0qYu9DU_nkDgMH0Vw-g&oe=6A30A990', descuento: 15 },
            { id: 5006, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-06', titulo: 'SÁBANA SILK PATTERN (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/719452462_886199207830738_9161911243992781798_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=102&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeF0ChB8dJf6GXzhepw4LYBiJGnCDjxMfJckacIOPEx8l6_Qt9ZJtv68XQu25naCCxThpnoUPbrOR95htl6jJkRD&_nc_ohc=swEjyLTwWegQ7kNvwGVvhbT&_nc_oc=AdrtEMFVBdV9LqZgENVdalb5lFNf9XXUC5EG4J4frqnrBx6-e7f6Ri1-A-3JczOHvkQ&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=VySGoUAx8z2GaKZKOR3TNQ&_nc_ss=7b2a8&oh=00_Af_fzCDolKaEOmx2GW92JA6dAIg4JICgeHWTTdvlg6Kuyw&oe=6A309CDC', descuento: 15 },
            { id: 5007, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-07', titulo: 'SÁBANA SUEÑO DISEÑO (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/721759020_886199264497399_8587345825147619520_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=108&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeEobjnF4XUF8OIE9IjIqJGySd4ILjPOtZNJ3gguM861kzJ5PpRc0o7Mp_PX8BtXsKWL1GTnhF9cwvyRwvR05pbx&_nc_ohc=a7Am_A-6MYEQ7kNvwFLAzHy&_nc_oc=AdpskoOlcIZAoYj0NjUVS35tu916f0Nfuiy0gGqPHXxRtSXYld5IWG1xXEQAKhm-xz8&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=EqfRmBKYlWY9me2kkC58qg&_nc_ss=7b2a8&oh=00_Af_YgYTBr-L3K2Tj5er0gvNdQYFLZFK0pJBDHyZgy9aMYw&oe=6A30B861', descuento: 15 },
            { id: 5008, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-08', titulo: 'SÁBANA ECO COLOR (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/722030823_886199287830730_5775418264529496675_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=111&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeErfBPI3sbvftu65kE_lhB349C9fpGN-cPj0L1-kY35wxEj7UGvuTcZrOO_kDjBZOr5PMVa8Z0levgEftr1o8oN&_nc_ohc=k6hex1uGbrMQ7kNvwHFnZun&_nc_oc=AdpLEFHktw0EISYOybfKXZdldwsw4ir4hpbJvK18xxLTb5YDgXoWyF-p471y8y2xCRw&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=rj1wooCeiFhHMVFnXn9TlQ&_nc_ss=7b2a8&oh=00_Af_CSp412dgBYx82z6v5_6R4shOyjQzslfSsrNdcwTZb-w&oe=6A308B91', descuento: 15 },
            { id: 5009, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-09', titulo: 'SÁBANA FRESCO TRAZO (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/722935239_886199304497395_2659266890755184319_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=100&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeFXYnbSfYvwpQLcW3kGmdJlAhAXoJJAUqICEBegkkBSou54nQUyUj91l9fWkMnxRJ6wzhHxT-KaMeVkdK-aiU0a&_nc_ohc=kV88XVrEfOIQ7kNvwH5tmtA&_nc_oc=AdrvgThtt_NLW3TvmiCzyLLiZzpnGIee8lIA4wXZG91eSIJjR4jWMJU68otqTwDk6HA&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=pGOamOwQ0Fl370UDnnDJmg&_nc_ss=7b2a8&oh=00_Af_FYDpKCqwB1VaaNDbJwQ_vzKv6JKRNuWygcI_FOLa-sA&oe=6A30D147', descuento: 15 },
            { id: 5010, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-10', titulo: 'SÁBANA MICRO LONA (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/719548584_886199361164056_7998625576012787432_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=100&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeGFNKuryRShfh40NEQL-8fOEZkVhfdR9EARmRWF91H0QO-1OQXbkf0xP9F-Jx4YxpZ7oQD_Yeq4IzxJKqpbXfKS&_nc_ohc=uNjZOqy64q4Q7kNvwFbpqnm&_nc_oc=Adqe7cW8vN84_tawI2z7BI2kSyaCoeTG8Odl0oVU1qTcYPgqHNCNDrt4FD_7rVEafvs&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=6CwBDNbxfyGcIwurwlQY8g&_nc_ss=7b2a8&oh=00_Af_Ur5tpA0OyJTKydc960HOyoPp6enoGey2oEPYcPXm6Qg&oe=6A30D47E', descuento: 15 },
            { id: 5011, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-11', titulo: 'SÁBANA PURA FORMA (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/721466931_886199381164054_8272752386813079139_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=110&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeH7NTbNf1XN3NGC19EfT9syFRUII9RQggIVFQgj1FCCAiPXgIMpCdkJzLtn-qxcZcQBCFjowxQBIqHrFfim5d70&_nc_ohc=lYYZKPNKApAQ7kNvwGF8FqE&_nc_oc=AdqATdXjktxJqaqAdOmeeBDA7wJwjVdG4QSH-4vzoMn-c5tx34YlYP_rJpgf2xPdw-s&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=P_8BY9ljXPRvKnmKAVbiKw&_nc_ss=7b2a8&oh=00_Af9ixB8ZOogpGEPS7ecuR5cYTqkQGtaXORdeLKJL21bUYA&oe=6A30D4AB', descuento: 15 },
            { id: 5012, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-12', titulo: 'SÁBANA AURA PRINT (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/722996776_886199401164052_1780607619500035830_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=110&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeHlviv8pVrzno2XbTIhd9i10ObxLMrNnVXQ5vEsys2dVfqs8OFaLctcF1p5IN3vB6bSYHMQMI6mknKpIg9FDhPj&_nc_ohc=Vp-H7KEpiKAQ7kNvwHS8tlB&_nc_oc=AdollvMDFfClUDoClXNbTRmiiQyNRKgC3g9FhHcPleTQHgWIHv1fp-8mxia19jOSzS4&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=VAwmCy5gt_9gWfmUG-yQaQ&_nc_ss=7b2a8&oh=00_Af9XkvYXHYi_W1MjUT9ZVkbkWTArn9hJNeD1Dq7Gp78BtQ&oe=6A30DBEA', descuento: 15 },
            { id: 5013, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-13', titulo: 'SÁBANA SUAVE ARTE (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/721737137_886199551164037_2235985980478758255_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=100&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeEtBYxQptVhmVnL9JvUCN5WKjDtShW-vYgqMO1KFb69iFPLiT0VpgH4yHFoDc9lPxVrjtJZu0sAI2269sY8NCjJ&_nc_ohc=M0myBnYqac0Q7kNvwHijqnN&_nc_oc=AdoZizgXrquMsqro-3cTtOPIXvGHKGR2VBcnG0GNZAPreZw5WhIgGl8NTBNW_-xfn5k&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=rbAh1r_SElB1Jq_oi7lcgA&_nc_ss=7b2a8&oh=00_Af-cVAH_VXSvdTjDCTJAj0V1G_bTwSAGWIqYkUh8bFTBzw&oe=6A30BE04', descuento: 15 },
            { id: 5014, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-14', titulo: 'SÁBANA BELLA MICRO (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/720192793_886199454497380_5378897122060185986_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=107&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeEMgnahlu4fvNi9k9mMeHmrUyS_QoATmg1TJL9CgBOaDaUw8Ds9wxqUjDMo9KvOXxrV-71Fpzx6LM7MbCUnRu7A&_nc_ohc=a2MKydOQWEcQ7kNvwGszfEr&_nc_oc=Ado08-ZZYHGi1Dmodl9yW403jHXYo14rCpXdABNRWeIJE6MVbT7sTOtRuIs3l7IjznE&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=mkJ6RZr-ukJIKOjGnABalg&_nc_ss=7b2a8&oh=00_Af-tPjxwUkrY-ZMlDF4A4nlWlN5T44SCcUoCCFIURBa91A&oe=6A30BB7D', descuento: 15 },
            { id: 5015, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-15', titulo: 'SÁBANA TRAMA VIVA (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/719771231_886199477830711_9023459652606757776_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=107&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeFToO23ex9dGz1LaL2XishiORFCmGP26IM5EUKYY_bog7Yidi1Q1tfIkkwbiP8ToA-TedWT_VJ6NwqS_4lC5FOi&_nc_ohc=BJVWf-sdANMQ7kNvwGqo22_&_nc_oc=AdpwNMw5emGIi4bbbT1Jv-xW66vQ1EpqsyLU1ulMZzT_lOlU3uWRbKDLtMzfIWKVgmY&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=Qn0qSVfzG-M2oBjVbfrKRg&_nc_ss=7b2a8&oh=00_Af9tmjGg7fY65ffnnNe59DNdW9eFmskWXEQeRQg77myO_Q&oe=6A30BFC7', descuento: 15 },
            { id: 5016, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-16', titulo: 'SÁBANA LINEN GLAM (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/721349256_886199517830707_7592881648313906941_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=107&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeEsibW1sfZebdeku4PTKXJNDXkCqV0_2rINeQKpXT_asvv-9g6yrmQJWi7gSHD0LN7aO7c0HHVwMuHDghIwesD8&_nc_ohc=RJ8ggAQJPWIQ7kNvwFBUBGp&_nc_oc=AdqxHqGsugE_vadF4wE-OzTdyO1ptGJ-vTzmEz3qGKlDY_0PtXTKi-Ks_gUwQ4ZEAas&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=mc7nf9XQNxXnWUs2M32xeA&_nc_ss=7b2a8&oh=00_Af8cWJ57-THJBobVdpmliBznTNRCQIG6j3FJhIfu0x1nzA&oe=6A30D54F', descuento: 15 },
            { id: 5017, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-17', titulo: 'SÁBANA MICRO LIENZO (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/719864917_886199567830702_1890529617709125510_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=104&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeGz1I5VCLWiNAIJ_Cc_WZQa8NNw6g8ccN_w03DqDxxw33U-RicMM5EIUwi52HneyqHFuUwibKZADEDYVB7CIwb8&_nc_ohc=Sip32sltP4UQ7kNvwERe5tP&_nc_oc=Adqts4Z6jH0p9SleelD_-j9aAZ8XiQlg6RzaZ2ozCmS6RbHB5HihycuOHHanb-6S3yA&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=1Tx-g58MIM4F4or0FIaIiA&_nc_ss=7b2a8&oh=00_Af-YtVmS8Q5RTGo4e7lHHwW9sREO0M1MYAoRFvk-3-9TMw&oe=6A30B4BC', descuento: 15 },
            { id: 5018, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-18', titulo: 'SÁBANA STYLUS CONFORT (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/720959880_886199611164031_1243353095101384817_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=102&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeGSRuumaQvoz9gs7bp-sCPlO34hp-k2VSQ7fiGn6TZVJErAYZl1IbDlsYZ6uEpodjdB5Cim9OQOZhDIvbUM-aK6&_nc_ohc=v_ZiED_uop8Q7kNvwHqqChb&_nc_oc=AdqoHr9QLqUUPSqRUAt87qhP4Uj6j9bs8DO28J2_vicy_S0TFJ7l7JZccyxKxEvNDJk&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=shE82zeoKLOFHlZ_iRYyHw&_nc_ss=7b2a8&oh=00_Af_tL3ZE4O1digxxqXd4ChZU4RDBkTLMm9g2fwSzN0sEgg&oe=6A30A586', descuento: 15 },
            { id: 5019, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-19', titulo: 'SÁBANA CREA SUEÑOS (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/720524400_886199641164028_6269666072446707795_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=100&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeEurqPbpm9xaci6HKlllbE1UoEKuAeXn0JSgQq4B5efQtwTTI2RY7skLcddNSk8uGHorhm1_7h4hbu5DMC2BU9a&_nc_ohc=g8m-HYszI98Q7kNvwFAEzUR&_nc_oc=AdqGpxkXia_-KghzBrBCYo5dAHjZ3JdDSiMPFfL1Qd5Va0a1_6GOBskK9SHwTSbLqcU&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=rxVjiwG9J0RyT1GTsP3lAw&_nc_ss=7b2a8&oh=00_Af8ocfsyy6fJDpcpnRcbmz0CejC01TmDpeWArNV0mTCNJQ&oe=6A30C01D', descuento: 15 },
            { id: 5020, cat: 'sabanas', sub: 'sale', ref: 'SAB-SALE-20', titulo: 'SÁBANA MAXI PRINT (LIQUIDACIÓN)', desc: 'Últimas unidades disponibles con precio de liquidación de temporada.', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/722147751_886199654497360_7417355755133080656_n.jpg?stp=dst-jpg_tt6&cstp=mx1080x1080&ctp=s1080x1080&_nc_cat=106&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeHmoRhjE9BKowFUDNeOiIuhiPoO2XN5nhSI-g7Zc3meFNzIPOvCRx4tlxqhMnoim2sAmnP5l_Sly779_HKt7PVq&_nc_ohc=l8O_t-b_5wUQ7kNvwGF-7bZ&_nc_oc=AdoB3W3IV5th8C3y4IMffhC2NoJ3eCUSviLg_mUI2AHLGaD8uRSGALLI2cQzRFs8lJQ&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=dTY76eXVLhK0GH-wtsZxmA&_nc_ss=7b2a8&oh=00_Af_sg5PMmsDN96AbrQegUSePw4DKNpaHNm5LbakQWJT8gA&oe=6A30BD44', descuento: 15 },

            
            { id: 20, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-01', titulo: 'SÁBANA NIKO', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2112-large_default/sabana-niko.jpg' },
            { id: 21, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-02', titulo: 'SÁBANA LINDA BLUSH', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2108-large_default/sabana-linda-blush.jpg' },
            { id: 22, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-03', titulo: 'SÁBANA VERONICA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2100-large_default/sabana-victoria.jpg' },
            { id: 23, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-04', titulo: 'SÁBANA LINDA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2104-large_default/sabana-linda.jpg' },
            { id: 24, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-05', titulo: 'SÁBANA BERLIN ONIX', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2096-large_default/sabana-berlin-onix.jpg' },
            { id: 25, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-06', titulo: 'SÁBANA ZAIRA TURQUESA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2052-large_default/sabana-zaira-turquesa.jpg' },
            { id: 26, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-07', titulo: 'SÁBANA BERLIN', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2092-large_default/sabana-berlin.jpg' },
            { id: 27, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-08', titulo: 'SÁBANA ZAIRA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en the image. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2048-large_default/sabana-zaira.jpg' },
            { id: 28, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-09', titulo: 'SÁBANA OSLO SILVER', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2044-large_default/sabana-oslo-silver.jpg' },
            { id: 29, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-10', titulo: 'SÁBANA SHANNON PINK', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1975-large_default/sabana-shannon-pink.jpg' },
            { id: 30, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-11', titulo: 'SÁBANA OSLO', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2040-large_default/sabana-oslo.jpg' },
            { id: 31, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-12', titulo: 'SÁBANA ODESSA ONIX', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1967-large_default/sabana-odessa-onix.jpg' },
            { id: 32, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-13', titulo: 'SÁBANA EBBA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1908-large_default/sabana-ebba.jpg' },
            { id: 33, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-14', titulo: 'SÁBANA TAMPA GREEN', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1855-large_default/sabana-tampa-green.jpg' },
            { id: 34, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-15', titulo: 'SÁBANA CAMILLE', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1843-large_default/sabana-camille.jpg' },
           
            { id: 2, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-01', titulo: 'SÁBANA DALIA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1465-large_default/dalia.jpg' },
            { id: 3, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-02', titulo: 'SÁBANA HORTENSIA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/948-large_default/ortencia.jpg' },
            { id: 4, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-03', titulo: 'SÁBANA MILÁN', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/841-large_default/sabana-milan.jpg' },
            { id: 5, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-04', titulo: 'SÁBANA LISBOA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/163-large_default/lisboa.jpg' },
            { id: 6, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-05', titulo: 'SÁBANA CANADÁ', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1744-large_default/canada.jpg' },
            { id: 7, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-06', titulo: 'SÁBANA MOSCÚ', desc: 'Juego de sábanas unicolor en calidad texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1746-large_default/moscu.jpg' },
            { id: 8, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-07', titulo: 'SÁBANA RAQUEL', desc: 'Juego de sábanas unicolor en calidad texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábanas, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/151-large_default/raquel.jpg' },
            { id: 9, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-08', titulo: 'SÁBANA VIVIANA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/155-large_default/vivian.jpg' },
            { id: 10, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-9', titulo: 'SÁBANA ARIANA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/149-large_default/ariana.jpg' },

            { id: 11, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-01', titulo: 'SÁBANA NIKO', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2112-large_default/sabana-niko.jpg' },
            { id: 12, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-02', titulo: 'SÁBANA TRANSFORMERS', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1777-large_default/sabana-transformers.jpg' },
            { id: 13, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-03', titulo: 'SÁBANA MATER', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1369-large_default/sabana-mater.jpg' },
            { id: 14, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-04', titulo: 'SÁBANA STAR', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1041-large_default/sabana-star.jpg' },
            { id: 15, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINA-01', titulo: 'SÁBANA EBBA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1908-large_default/sabana-ebba.jpg' },
            { id: 16, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINA-02', titulo: 'SÁBANA ABBY', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1540-large_default/sabana-abby.jpg' },
            { id: 17, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINA-03', titulo: 'SÁBANA RITA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1232-large_default/sabana-rita.jpg' },
            
            { id: 50, cat: 'sabanas_exclusivas', sub: '200-hilos', ref: 'SAB-EXCLU-01', titulo: '🚱PROTECTOR  TOALLA  100% IMPERMEABLE🚱', desc: '💧Protector  toalla suave al tacto, para colchon con cierre completo, anti acaros 100% impermeable💦', img: 'https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/722521120_887276141056378_4917117391306092385_n.jpg?stp=dst-jpg_tt6&cstp=mx750x750&ctp=s750x750&_nc_cat=102&ccb=1-7&_nc_sid=127cfc&_nc_eui2=AeG0u7j0oR6XbTt-Zp8wwPR_wIa01m11cYTAhrTWbXVxhAI7bQ8r1CQt5nTPM8fR3OmnQIuobA6Yqz4zyZAZo7el&_nc_ohc=nUbQq42E8ekQ7kNvwGYebLd&_nc_oc=AdqNiZXMjtM7ndQNVxmPFM9LHjFHckjnV6fpXLVO2TJsmibCJQu6rd-Jnz0hxW5sYHk&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=A6woAlMdfHx_wKAX0cbQ_w&_nc_ss=7b2a8&oh=00_Af9LSAuHBdJXDQ3MMPm6sVkvurMiL9L5rskDn864MnbRmQ&oe=6A31C5F4', },

            { id: 1018, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-01', titulo: 'CORTINAS CANADÁ', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1954-large_default/c-canada.jpg' },
            { id: 1019, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-02', titulo: 'CORTINAS MOSCÚ', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/664-large_default/c-moscu.jpg' },
            { id: 1020, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-03', titulo: 'CORTINAS NIKO', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2121-large_default/cortinas-niko.jpg' },
            { id: 1021, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-04', titulo: 'CORTINAS LINDA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2119-large_default/cortinas-linda.jpg' },
            { id: 1022, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-05', titulo: 'CORTINAS VERONICA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2117-large_default/cortinas-victoria.jpg' },
            { id: 1023, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-06', titulo: 'CORTINAS BERLIN', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2115-large_default/cortinas-berlin.jpg' },
            { id: 1024, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-07', titulo: 'CORTINAS ZAIRA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2059-large_default/cortinas-zaira.jpg' },
            { id: 1025, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-08', titulo: 'CORTINAS OSLO', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2057-large_default/cortinas-oslo.jpg' },
            { id: 1026, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-09', titulo: 'CORTINAS SHANNON', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1982-large_default/cortinas-shannon.jpg' },
            { id: 1027, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-10', titulo: 'CORTINAS EBBA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1923-large_default/cortinas-ebba.jpg' },
            { id: 1028, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-11', titulo: 'CORTINAS TRANSFORMERS', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1786-large_default/cortinas-transformers.jpg' },
            { id: 1029, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-12', titulo: 'CORTINAS ABBY', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1549-large_default/cortinas-abby.jpg' },
            { id: 1030, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-13', titulo: 'CORTINAS MATER', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1378-large_default/cortinas-mater.jpg' },
            { id: 1031, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-14', titulo: 'CORTINAS RITA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1241-large_default/cortinas-rita.jpg' },
            { id: 1032, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-25', titulo: 'CORTINAS HORTENSIA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1052-large_default/-cortinas-hortensia-.jpg' },
            { id: 1033, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-17', titulo: 'CORTINAS STAR', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1050-large_default/cortinas-star.jpg' },
            { id: 1034, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-18', titulo: 'CORTINAS ARIANA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/995-large_default/cortinas-ariana.jpg' },
            { id: 1035, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-19', titulo: 'CORTINAS VERONA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/652-large_default/c-verona.jpg' },
          
            { id: 1036, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-01', titulo: 'CORTINAS TRANSFORMERS', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1786-large_default/cortinas-transformers.jpg' },
            { id: 1037, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-02', titulo: 'CORTINAS NIKO', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2121-large_default/cortinas-niko.jpg' },
            { id: 1038, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-03', titulo: 'CORTINAS EBBA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1923-large_default/cortinas-ebba.jpg' },
            { id: 1039, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-04', titulo: 'CORTINAS ABBY', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1549-large_default/cortinas-abby.jpg' },
            { id: 1040, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-05', titulo: 'CORTINAS STAR', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1050-large_default/cortinas-star.jpg' },

            { id: 1101, cat: 'cortinas', sub: 'clasica', ref: 'COR-EXCLU-02', titulo: 'Cortina Blackout Premium Neón', desc: 'Bloqueo total de luz solar (100% Blackout) con ojales reforzados y acabados de lujo.', img: 'https://dalotex.com.co/2119-large_default/cortinas-linda.jpg' },   

            { id: 2001, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-01', titulo: 'COLCHA DOBLE FAZ SHANNON', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/2143-large_default/colcha-shannon.jpg' },
            { id: 2002, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-02', titulo: 'COLCHA DOBLE FAZ ODESSA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/2139-large_default/colcha-odessa.jpg' },
            { id: 2003, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-03', titulo: 'COLCHA DOBLE FAZ EBBA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/2082-large_default/colcha-ebba.jpg' },
            { id: 2004, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-04', titulo: 'COLCHA DOBLE FAZ ALEJANDRÍA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/2078-large_default/colcha-alejandria.jpg' },
            { id: 2005, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-05', titulo: 'COLCHA DOBLE FAZ TAMPA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/2014-large_default/colcha-tampa.jpg' },
            { id: 2006, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-06', titulo: 'COLCHA DOBLE FAZ HORTENSIA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/1949-large_default/colcha-hortensia.jpg' },
            { id: 2007, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-07', titulo: 'COLCHA DOBLE FAZ LUCIA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/1884-large_default/colcha-lucia.jpg' },
            { id: 2008, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-08', titulo: 'COLCHA DOBLE FAZ SILVER', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/1882-large_default/colcha-silver.jpg' },
            { id: 2009, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-09', titulo: 'COLCHA DOBLE FAZ RAQUEL', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/1826-large_default/colcha-raquel.jpg' },
            { id: 2010, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-10', titulo: 'COLCHA DOBLE FAZ LISBOA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/1814-large_default/colcha-lisboa.jpg' },
            { id: 2011, cat: 'acolchados', sub: 'colcha-espanola', ref: 'ACO-ESP-11', titulo: 'COLCHA DOBLE FAZ CANADA', desc: 'Diseño y confección tipo doble faz con relieves texturizados de lujo.', img: 'https://dalotex.com.co/1810-large_default/colcha-canada.jpg' },
        ];

        let categoriaActual = 'sabanas';
        let subcategoriaActual = 'matrimonial';
        let carrito = [];
        let productoSeleccionadoModal = null;

        // Renderizado dinámico del bloque cronograma
        const cronogramaHTML = `
            <div class="paso-item resaltado">
                <div class="paso-numero">1</div>
                <div class="paso-texto"><strong>Elige tus productos</strong> favoritos del catálogo y añádelos al pedido.</div>
            </div>
           
             <div class="paso-item">
                <div class="paso-numero">2</div>
                <div class="paso-texto">Envía tu orden, y comprovante de pago    por WhatsApp. <span class="alerta-roja">¡Despachamos de inmediato!</span></div>
            </div>
            <div class="paso-item resaltado">
                <div class="paso-numero">3</div>
                <div class="paso-texto"><strong> Tus productos</strong> llegaran en un plaso de <span class="alerta-roja">6 a 7 dias habiles</span>.</div>
            </div>

            
        `;
        document.getElementById('mensaje-fomo').innerHTML = cronogramaHTML;

        function cambiarCategoria(cat, btn) {
            categoriaActual = cat;
            document.querySelectorAll('.btn-cat').forEach(b => b.classList.remove('activo'));
            btn.classList.add('activo');
            
            document.querySelectorAll('.subcat-wrapper').forEach(w => w.classList.remove('activo'));
            
            const wrapper = document.getElementById(`sub-${cat}`);
            if (wrapper) {
                wrapper.classList.add('activo');
                const primerBtn = wrapper.querySelector('.btn-subcat');
                if (primerBtn) {
                    primerBtn.click();
                }
            } else {
                subcategoriaActual = '';
                renderizarProductos();
            }
        }

        function filtrarSubcategoria(sub, btn) {
            subcategoriaActual = sub;
            if(btn) {
                const parent = btn.parentElement;
                parent.querySelectorAll('.btn-subcat').forEach(b => b.classList.remove('activo'));
                btn.classList.add('activo');
            }
            renderizarProductos();
        }

        // MOTOR REVISADO DE PRECIOS Y DESCUENTOS EN TIEMPO REAL
        function obtenerPreciosProducto(prod, medidaNombre) {
            const listaMedidas = opcionesMedidas[prod.cat] || opcionesMedidas['sabanas'];
            const medidaObj = listaMedidas.find(m => m.nombre === medidaNombre) || listaMedidas[0];
            
            const precioBase = medidaObj.precio;
            let precioFinal = precioBase;
            let ahorro = 0;

            if (prod.descuento && prod.descuento > 0) {
                ahorro = Math.round(precioBase * (prod.descuento / 100));
                precioFinal = precioBase - ahorro;
            }

            return {
                base: precioBase,
                final: precioFinal,
                ahorro: ahorro,
                medida: medidaObj.nombre
            };
        }

        function renderizarProductos(productosFiltrados = null) {
            const lista = productosFiltrados || productos.filter(p => p.cat === categoriaActual && (!subcategoriaActual || p.sub === subcategoriaActual));
            const contenedor = document.getElementById('contenedor-productos');
            contenedor.innerHTML = '';

            if(lista.length === 0) {
                contenedor.innerHTML = `<p style="text-align:center; grid-column: 1/-1; color: var(--texto-secundario); padding: 20px;">No se encontraron productos en esta sección.</p>`;
                return;
            }

            lista.forEach(prod => {
                const listaMedidas = opcionesMedidas[prod.cat] || opcionesMedidas['sabanas'];
                const medidaInicial = listaMedidas[0].nombre;
                const calc = obtenerPreciosProducto(prod, medidaInicial);

                // NUEVO BADGE LLAMATIVO (MANTENIDO CON NUEVO ESTILO CSS)
                let badgeHTML = prod.descuento ? `<div class="badge-descuento">${prod.descuento}%</div>` : '';
                
                // RENDERIZADO DE PRECIOS CORREGIDO
                let renderPrecio = prod.descuento 
                    ? `<span class="precio-antes">$${calc.base.toLocaleString()}</span><span class="precio-actualizado">$${calc.final.toLocaleString()}</span>`
                    : `$${calc.final.toLocaleString()}`;
                
                // NUEVO ESTILO DE AHORRO (MANTENIDO CON NUEVO ESTILO CSS)
                let renderAhorro = prod.descuento ? `<span class="alerta-ahorro" id="ahorro-card-${prod.id}">Ahorras: $${calc.ahorro.toLocaleString()}</span>` : '';

                // Añadir clase especial si tiene descuento
                let claseDescuento = prod.descuento ? 'tiene-descuento' : '';

                const card = document.createElement('div');
                card.className = `producto-card ${claseDescuento}`;
                card.innerHTML = `
                    ${badgeHTML}
                    <div class="producto-img-contenedor" onclick="verDetalleProducto('${prod.id}')">
                        <img src="${prod.img}" alt="${prod.titulo}" class="producto-img" loading="lazy">
                    </div>
                    <div class="producto-info">
                        <span class="producto-ref">${prod.ref}</span>
                        <h3 class="producto-titulo" onclick="verDetalleProducto('${prod.id}')">${prod.titulo}</h3>
                        
                        <select class="select-medida" id="select-medida-${prod.id}" onchange="cambiarMedidaCard('${prod.id}')">
                            ${listaMedidas.map(m => `<option value="${m.nombre}">${m.nombre}</option>`).join('')}
                        </select>

                        ${renderAhorro}
                        <div class="producto-precio" id="precio-card-${prod.id}">
                            ${renderPrecio}
                        </div>
                        <button class="btn-agregar" onclick="agregarAlPedidoDesdeCard('${prod.id}')">Agregar al Pedido</button>
                    </div>
                `;
                contenedor.appendChild(card);
            });
        }

        function cambiarMedidaCard(id) {
            const prod = productos.find(p => p.id == id || p.id === id);
            const select = document.getElementById(`select-medida-${id}`);
            const calc = obtenerPreciosProducto(prod, select.value);

            const contenedorPrecio = document.getElementById(`precio-card-${id}`);
            const contenedorAhorro = document.getElementById(`ahorro-card-${id}`);

            if(prod.descuento) {
                // Se añade clase precio-actualizado para efecto visual
                contenedorPrecio.innerHTML = `<span class="precio-antes">$${calc.base.toLocaleString()}</span><span class="precio-actualizado">$${calc.final.toLocaleString()}</span>`;
                if(contenedorAhorro) contenedorAhorro.innerText = `Ahorras: $${calc.ahorro.toLocaleString()}`;
            } else {
                contenedorPrecio.innerHTML = `<span class="precio-actualizado">$${calc.final.toLocaleString()}</span>`;
            }
            
            // Quitar clase de animación después de que termine para poder repetirla
            setTimeout(() => {
                contenedorPrecio.querySelectorAll('.precio-actualizado').forEach(el => el.classList.remove('precio-actualizado'));
            }, 600);
        }

        function verDetalleProducto(id) {
            const prod = productos.find(p => p.id == id || p.id === id);
            productoSeleccionadoModal = prod;

            document.getElementById('det-img').src = prod.img;
            document.getElementById('det-ref').innerText = prod.ref;
            document.getElementById('det-titulo').innerText = prod.titulo;
            document.getElementById('det-desc').innerText = prod.desc;

            const select = document.getElementById('det-select-medida');
            const listaMedidas = opcionesMedidas[prod.cat] || opcionesMedidas['sabanas'];
            select.innerHTML = listaMedidas.map(m => `<option value="${m.nombre}">${m.nombre}</option>`).join('');

            actualizarPrecioModal();

            document.getElementById('det-btn-agregar').onclick = () => {
                const calc = obtenerPreciosProducto(prod, select.value);
                agregarAlCarrito(prod, calc.medida, calc.final);
                cerrarModal('modal-detail');
            };

            document.getElementById('modal-detail').style.display = 'flex';
        }

        function actualizarPrecioModal() {
            if (!productoSeleccionadoModal) return;
            const select = document.getElementById('det-select-medida');
            const calc = obtenerPreciosProducto(productoSeleccionadoModal, select.value);
            
            const contenedorPrincipal = document.getElementById('det-contenedor-precio');
            // const contenedorPrecioEstandar = document.getElementById('det-precio'); // No usado pero mantenido por referencia

            if(productoSeleccionadoModal.descuento) {
                // Diseño especial para descuento en modal (NUEVO ESTILO CSS MANTENIDO)
                contenedorPrincipal.innerHTML = `
                    <div class="contenedor-precio-modal-descuento">
                        <span class="tag-modal-descuento">OFERTA ESPECIAL 🔥</span>
                        <div style="display:flex; align-items:center; flex-wrap:wrap; gap:5px;">
                            <span class="precio-antes" style="font-size:1.1rem; margin-right:10px;">$${calc.base.toLocaleString()}</span>
                            <span class="precio-actualizado" style="font-size:2rem; margin:0; font-weight:900; color:var(--rojo-descuento-neon); text-shadow: 0 0 10px rgba(255,23,68,0.7);">$${calc.final.toLocaleString()}</span>
                        </div>
                        <div style="font-size:0.95rem; color:#ffea00; font-weight:bold; margin-top:10px; display:flex; align-items:center; gap:8px;">
                            <span style="animation: flickerFlame 0.5s infinite alternate;">🔥</span>
                            <span>¡Ahorras un ${productoSeleccionadoModal.descuento}%!</span>
                            <span style="background-color:var(--rojo-descuento-neon); color:white; padding:3px 8px; border-radius:20px; box-shadow: 0 0 8px var(--rojo-descuento-neon);">-$${calc.ahorro.toLocaleString()}</span>
                        </div>
                    </div>
                `;
            } else {
                // Volver a diseño estándar si no hay descuento
                contenedorPrincipal.innerHTML = `<div id="det-precio" class="producto-precio" style="font-size:1.6rem; margin-top:10px; font-weight:800; color:var(--precio-verde);">$${calc.final.toLocaleString()}</div>`;
            }
        }

        function agregarAlPedidoDesdeCard(id) {
            const prod = productos.find(p => p.id == id || p.id === id);
            const select = document.getElementById(`select-medida-${id}`);
            const calc = obtenerPreciosProducto(prod, select.value);
            agregarAlCarrito(prod, calc.medida, calc.final);
            
            // Pequeño feedback visual en el botón
            const btn = document.querySelector(`#precio-card-${id}`).parentElement.querySelector('.btn-agregar');
            const textoOriginal = btn.innerText;
            btn.innerText = "¡Añadido! ✅";
            btn.style.background = "linear-gradient(90deg, #2e7d32, #66bb6a)";
            setTimeout(() => {
                btn.innerText = textoOriginal;
                btn.style.background = "";
            }, 1500);
        }

        // RESTO DE LÓGICA DE CARRITO Y CHECKOUT MANTENIDA IGUAL
        function agregarAlCarrito(prod, medida, precioCobrado) {
            const itemExistente = carrito.find(item => item.id === prod.id && item.medida === medida);
            if(itemExistente) {
                itemExistente.cant++;
            } else {
                carrito.push({
                    id: prod.id,
                    titulo: prod.titulo,
                    ref: prod.ref,
                    medida: medida,
                    precio: precioCobrado,
                    cant: 1
                });
            }
            actualizarBarraCarrito();
        }

        function actualizarBarraCarrito() {
            const cantTotal = carrito.reduce((acc, item) => acc + item.cant, 0);
            const dineroTotal = carrito.reduce((acc, item) => acc + (item.precio * item.cant), 0);

            document.getElementById('carrito-cant').innerText = `${cantTotal} Producto${cantTotal !== 1 ? 's' : ''}`;
            document.getElementById('carrito-total').innerText = `$${dineroTotal.toLocaleString()}`;
            
            // Animación en la barra para avisar que cambió
            const barra = document.querySelector('.barra-carrito');
            barra.style.animation = 'tildePulso 0.3s ease 2';
            setTimeout(() => barra.style.animation = '', 600);
        }

        function abrirCheckout() {
            if(carrito.length === 0) {
                alert("Tu carrito está vacío. Agrega productos primero.");
                return;
            }

            const contenedor = document.getElementById('checkout-items');
            contenedor.innerHTML = '';

            carrito.forEach((item, index) => {
                const row = document.createElement('div');
                row.className = 'checkout-item';
                row.innerHTML = `
                    <div class="checkout-item-info">
                        <strong>${item.titulo}</strong>
                        <span style="font-size:0.75rem; color:#666;">Medida: ${item.medida} | Cant: ${item.cant}</span>
                    </div>
                    <div class="checkout-item-acciones">
                        <span style="font-weight:bold; color:var(--precio-verde);">$${(item.precio * item.cant).toLocaleString()}</span>
                        <button class="btn-eliminar" onclick="eliminarDelCarrito(${index})">&times;</button>
                    </div>
                `;
                contenedor.appendChild(row);
            });

            const dineroTotal = carrito.reduce((acc, item) => acc + (item.precio * item.cant), 0);
            document.getElementById('checkout-total').innerText = `$${dineroTotal.toLocaleString()}`;

            document.getElementById('modal-checkout').style.display = 'flex';
        }

        function eliminarDelCarrito(index) {
            carrito.splice(index, 1);
            actualizarBarraCarrito();
            if(carrito.length === 0) {
                cerrarModal('modal-checkout');
            } else {
                abrirCheckout();
            }
        }

        function controlarMetodoPago(val) {
            const infoBanco = document.getElementById('info-banco');
            if(val === 'Transferencia') {
                infoBanco.style.display = 'block';
            } else {
                infoBanco.style.display = 'none';
            }
        }

        function cerrarModal(id) {
            document.getElementById(id).style.display = 'none';
        }

        function ejecutarBusquedaCompleta() {
            const txt = document.getElementById('input-filtrar').value.toLowerCase().trim();
            if(!txt) {
                renderizarProductos();
                return;
            }

            const filtrados = productos.filter(p => 
                p.titulo.toLowerCase().includes(txt) ||
                p.ref.toLowerCase().includes(txt) ||
                p.desc.toLowerCase().includes(txt)
            );
            renderizarProductos(filtrados);
        }

        function procesarCompra() {
            const nombre = document.getElementById('cliente-nombre').value.trim();
            const direccion = document.getElementById('cliente-direccion').value.trim();
            const telefono = document.getElementById('cliente-telefono').value.trim();
            const pago = document.getElementById('pago-select').value;

            if(!nombre || !direccion || !telefono) {
                alert("Por favor completa los datos solicitados de envío.");
                return;
            }

            let msg = `🛍️ *NUEVO PEDIDO - DULCES SUEÑOS* 🛍️\n\n`;
            msg += `👤 *Cliente:* ${nombre}\n`;
            msg += `📍 *Dirección:* ${direccion}\n`;
            msg += `📞 *WhatsApp:* ${telefono}\n`;
            msg += `💳 *Método de Pago:* ${pago}\n\n`;
            msg += `📦 *PRODUCTOS SOLICITADOS:*\n`;

            carrito.forEach(item => {
                msg += `• ${item.titulo} (${item.medida}) x${item.cant} -> *$${(item.precio * item.cant).toLocaleString()}*\n`;
            });

            const dineroTotal = carrito.reduce((acc, item) => acc + (item.precio * item.cant), 0);
            msg += `\n💰 *TOTAL NETO A PAGAR: $${dineroTotal.toLocaleString()}*\n\n`;
            msg += `⚡ _Pedido generado desde el Catálogo Virtual_`;

            const urlWa = `https://api.whatsapp.com/send?phone=573189882787&text=${encodeURIComponent(msg)}`;
            window.open(urlWa, '_blank');
        }

        // Inicialización
        renderizarProductos();
    </script>
</body>
</html>
