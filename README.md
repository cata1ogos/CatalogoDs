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
            justify: (135deg, #fdfbf7 0%, #eae5d9 100%);
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
            gap: 5px;
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
        <img src="  https://scontent.fnva2-1.fna.fbcdn.net/v/t39.30808-6/735210800_122181514202612503_220770715253923257_n.jpg?stp=dst-jpg_tt6&cstp=mx2048x2048&ctp=s2048x2048&_nc_cat=108&ccb=1-7&_nc_sid=6ee11a&_nc_eui2=AeHwQYrlJfoWciTa8e4M374T3AswG0Ze0UHcCzAbRl7RQZXZ2cssW6xY2gzxBsS5QrTVYmZKZwU8FzQmdyaphBst&_nc_ohc=0MFbH8Pf2xgQ7kNvwHYi53k&_nc_oc=AdryulGiY0DklwEm6XoXxap1ZAVc3MzLXxfEc26mV_Apt7nRfQ1h3P9nH3TL7nJZP9g&_nc_zt=23&_nc_ht=scontent.fnva2-1.fna&_nc_gid=bMXh0oxqdLD8gouAYrhB4A&_nc_ss=7b2a8&oh=00_AQAS0pXDotHpSLV_Aoht8J3qOOzOIZ1zECRPPrpCmwdTug&oe=6A4C7022" alt="Dulces Sueños - Hogar, Sábanas & Cortinas" class="logo-img">
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
        
    </nav>

    <div class="subcategorias-container">
       <div id="sub-sabanas" class="subcat-wrapper activo">
           
           

                <button class="btn-subcat" onclick="filtrarSubcategoria('matrimonial', this)" style="color: #000000; font-weight: bold; text-shadow: 0 0 5px rgba(255,23,68,0.5);">Matrimonial</button>
            <button class="btn-subcat" onclick="filtrarSubcategoria('unicolor', this)" style="color: #000000fb; font-weight: bold; text-shadow: 0 0 5px rgba(255,23,68,0.5);">Unicolor</button>
            <button class="btn-subcat" onclick="filtrarSubcategoria('infantil-nino', this)" style="color: #000000; font-weight: bold; text-shadow: 0 0 5px rgba(255,23,68,0.5);">Infantil</button>

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
                    <option value="MercadoPago">Mercado Pago (Link de Pago)</option>
                </select>
            </div>

            <div id="info-banco" class="info-transferencia">
                <strong>Paga de forma rápida y segura con Mercado Pago:</strong><br>
                Puedes realizar tu pago ingresando al siguiente enlace o preconando el boton de mercado pago oficial:<br>
                <a href="https://link.mercadopago.com.co/sabanasdulcesuenos" target="_blank" style="color: var(--precio-verde); font-weight: bold; text-decoration: underline;">link.mercadopago.com.co/sabanasdulcesuenos</a><br><br>
                *Adjunta el comprobante generado por la plataforma al enviar tu pedido por WhatsApp.
            </div>

            <button class="btn-enviar-wa">
              <a href="https://link.mercadopago.com.co/sabanasdulcesuenos" target="_blank" style="color: var(--precio-blanco); font-weight: bold; text-decoration: underline;">mercado pago </a>
            </button>

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
                { font: "240 x 240 Queen", precio: 160000  },
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
           
            { id: 20, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-01', titulo: 'SÁBANA NIKO', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2112-large_default/sabana-niko.jpg', descuento: 10 },
            { id: 21, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-02', titulo: 'SÁBANA LINDA BLUSH', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2108-large_default/sabana-linda-blush.jpg',descuento: 10 },
            { id: 22, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-03', titulo: 'SÁBANA VERONICA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2100-large_default/sabana-victoria.jpg',descuento: 10 },
            { id: 23, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-04', titulo: 'SÁBANA LINDA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2104-large_default/sabana-linda.jpg',descuento: 10 },
            { id: 24, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-05', titulo: 'SÁBANA BERLIN ONIX', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2096-large_default/sabana-berlin-onix.jpg',descuento: 10 },
            { id: 25, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-06', titulo: 'SÁBANA ZAIRA TURQUESA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2052-large_default/sabana-zaira-turquesa.jpg',descuento: 10 },
            { id: 26, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-07', titulo: 'SÁBANA BERLIN', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2092-large_default/sabana-berlin.jpg',descuento: 10 },
            { id: 27, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-08', titulo: 'SÁBANA ZAIRA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en the image. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2048-large_default/sabana-zaira.jpg',descuento: 10 },
            { id: 28, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-09', titulo: 'SÁBANA OSLO SILVER', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2044-large_default/sabana-oslo-silver.jpg', descuento: 10},
            { id: 29, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-10', titulo: 'SÁBANA SHANNON PINK', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1975-large_default/sabana-shannon-pink.jpg',descuento: 10 },
            { id: 30, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-11', titulo: 'SÁBANA OSLO', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2040-large_default/sabana-oslo.jpg',descuento: 10 },
            { id: 31, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-12', titulo: 'SÁBANA ODESSA ONIX', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1967-large_default/sabana-odessa-onix.jpg',descuento: 10 },
            { id: 32, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-13', titulo: 'SÁBANA EBBA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1908-large_default/sabana-ebba.jpg',descuento: 10 },
            { id: 33, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-14', titulo: 'SÁBANA TAMPA GREEN', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1855-large_default/sabana-tampa-green.jpg',descuento: 10 },
            { id: 34, cat: 'sabanas', sub: 'matrimonial', ref: 'SAB-MAT-15', titulo: 'SÁBANA CAMILLE', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1843-large_default/sabana-camille.jpg',descuento: 10 },
           
            { id: 2, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-01', titulo: 'SÁBANA DALIA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1465-large_default/dalia.jpg',descuento: 10 },
            { id: 3, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-02', titulo: 'SÁBANA HORTENSIA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/948-large_default/ortencia.jpg',descuento: 10  },
            { id: 4, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-03', titulo: 'SÁBANA MILÁN', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/841-large_default/sabana-milan.jpg',descuento: 10  },
            { id: 5, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-04', titulo: 'SÁBANA LISBOA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/163-large_default/lisboa.jpg',descuento: 10  },
            { id: 6, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-05', titulo: 'SÁBANA CANADÁ', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1744-large_default/canada.jpg',descuento: 10  },
            { id: 7, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-06', titulo: 'SÁBANA MOSCÚ', desc: 'Juego de sábanas unicolor en calidad texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1746-large_default/moscu.jpg',descuento: 10  },
            { id: 8, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-07', titulo: 'SÁBANA RAQUEL', desc: 'Juego de sábanas unicolor en calidad texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábanas, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/151-large_default/raquel.jpg' ,descuento: 10 },
            { id: 9, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-08', titulo: 'SÁBANA VIVIANA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/155-large_default/vivian.jpg',descuento: 10  },
            { id: 10, cat: 'sabanas', sub: 'unicolor', ref: 'SAB-UNICO-9', titulo: 'SÁBANA ARIANA', desc: 'Juego de sábanas unicolor en calidad microfibra texturizada, 100% garantizadas los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/149-large_default/ariana.jpg',descuento: 10  },

            { id: 11, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-01', titulo: 'SÁBANA NIKO', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/2112-large_default/sabana-niko.jpg',descuento: 15  },
            { id: 12, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-02', titulo: 'SÁBANA TRANSFORMERS', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1786-large_default/cortinas-transformers.jpg',descuento: 15  },
            { id: 13, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-03', titulo: 'SÁBANA MATER', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1369-large_default/sabana-mater.jpg' ,descuento: 15 },
            { id: 14, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINO-04', titulo: 'SÁBANA STAR', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1041-large_default/sabana-star.jpg',descuento: 15  },
            { id: 15, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINA-01', titulo: 'SÁBANA EBBA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1908-large_default/sabana-ebba.jpg',descuento: 15  },
            { id: 16, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINA-02', titulo: 'SÁBANA ABBY', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1540-large_default/sabana-abby.jpg' ,descuento: 15 },
            { id: 17, cat: 'sabanas', sub: 'infantil-nino', ref: 'SAB-NINA-03', titulo: 'SÁBANA RITA', desc: 'Juego de sábanas estampado, en calidad microfibra texturizada, 100% garantizadas ¡no se motosean ni se destiñen! los colores son tal cual están en la imagen. Consta de sábana, sobre sábana y dos fundas.', img: 'https://dalotex.com.co/1232-large_default/sabana-rita.jpg' ,descuento: 15 },
            

            { id: 1018, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-01', titulo: 'CORTINAS CANADÁ', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1954-large_default/c-canada.jpg',descuento: 15  },
            { id: 1019, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-02', titulo: 'CORTINAS MOSCÚ', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/664-large_default/c-moscu.jpg',descuento: 15  },
            { id: 1020, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-03', titulo: 'CORTINAS NIKO', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2121-large_default/cortinas-niko.jpg' ,descuento: 15 },
            { id: 1021, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-04', titulo: 'CORTINAS LINDA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2119-large_default/cortinas-linda.jpg',descuento: 15  },
            { id: 1022, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-05', titulo: 'CORTINAS VERONICA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2117-large_default/cortinas-victoria.jpg',descuento: 15  },
            { id: 1023, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-06', titulo: 'CORTINAS BERLIN', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2115-large_default/cortinas-berlin.jpg',descuento: 15  },
            { id: 1024, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-07', titulo: 'CORTINAS ZAIRA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2059-large_default/cortinas-zaira.jpg' ,descuento: 15 },
            { id: 1025, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-08', titulo: 'CORTINAS OSLO', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2057-large_default/cortinas-oslo.jpg',descuento: 15  },
            { id: 1026, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-09', titulo: 'CORTINAS SHANNON', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1982-large_default/cortinas-shannon.jpg',descuento: 15  },
            { id: 1027, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-10', titulo: 'CORTINAS EBBA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1923-large_default/cortinas-ebba.jpg' ,descuento: 15 },
            { id: 1028, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-11', titulo: 'CORTINAS TRANSFORMERS', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1786-large_default/cortinas-transformers.jpg',descuento: 15  },
            { id: 1029, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-12', titulo: 'CORTINAS ABBY', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1549-large_default/cortinas-abby.jpg',descuento: 15  },
            { id: 1030, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-13', titulo: 'CORTINAS MATER', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1378-large_default/cortinas-mater.jpg',descuento: 15  },
            { id: 1031, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-14', titulo: 'CORTINAS RITA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1241-large_default/cortinas-rita.jpg',descuento: 15  },
            { id: 1032, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-25', titulo: 'CORTINAS HORTENSIA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1052-large_default/-cortinas-hortensia-.jpg',descuento: 15  },
            { id: 1033, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-17', titulo: 'CORTINAS STAR', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1050-large_default/cortinas-star.jpg',descuento: 15  },
            { id: 1034, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-18', titulo: 'CORTINAS ARIANA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/995-large_default/cortinas-ariana.jpg' ,descuento: 15 },
            { id: 1035, cat: 'cortinas', sub: 'clasica', ref: 'COR-CLASIC-19', titulo: 'CORTINAS VERONA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/652-large_default/c-verona.jpg',descuento: 15  },
          
            { id: 1036, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-01', titulo: 'CORTINAS TRANSFORMERS', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1786-large_default/cortinas-transformers.jpg',descuento: 15  },
            { id: 1037, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-02', titulo: 'CORTINAS NIKO', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/2121-large_default/cortinas-niko.jpg',descuento: 15  },
            { id: 1038, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-03', titulo: 'CORTINAS EBBA', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1923-large_default/cortinas-ebba.jpg',descuento: 15  },
            { id: 1039, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-04', titulo: 'CORTINAS ABBY', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1549-large_default/cortinas-abby.jpg' ,descuento: 15 },
            { id: 1040, cat: 'cortinas', sub: 'infantiles', ref: 'COR-INFANT-05', titulo: 'CORTINAS STAR', desc: 'Las cortinas están dividida en dos paños cada paño mide 2.30 de ancho x 1.85cm de alto. ¡Más dos sujetadores de cortina!', img: 'https://dalotex.com.co/1050-large_default/cortinas-star.jpg' ,descuento: 15 },

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
                <div class="paso-texto">Envía tu orden, y comprobante de pago por WhatsApp. <span class="alerta-roja">¡Despachamos de inmediato!</span></div>
            </div>
            <div class="paso-item resaltado">
                <div class="paso-numero">3</div>
                <div class="paso-texto"><strong> Tus productos</strong> llegaran en un plazo de <span class="alerta-roja">6 a 7 dias habiles</span>.</div>
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
                // Buscamos el producto original por id para obtener la URL de su imagen
                const prodOriginal = productos.find(p => p.id == item.id);
                const imagenUrl = prodOriginal ? prodOriginal.img : '';

                const row = document.createElement('div');
                row.className = 'checkout-item';
                row.innerHTML = `
                    <div style="display: flex; align-items: center; gap: 10px; width: 70%;">
                        <img src="${imagenUrl}" alt="${item.titulo}" style="width: 50px; height: 50px; object-fit: cover; border-radius: 6px; flex-shrink: 0;">
                        <div class="checkout-item-info" style="max-width: 100%;">
                            <strong>${item.titulo}</strong>
                            <span style="font-size:0.75rem; color:#666;">Medida: ${item.medida} | Cant: ${item.cant}</span>
                        </div>
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
            if(val === 'MercadoPago') {
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
            msg += `💳 *Método de Pago:* ${pago === 'MercadoPago' ? 'Mercado Pago' : pago}\n\n`;
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
