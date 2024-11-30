# PF_Sistema-Experto_ML
Sistema Experto es una plataforma web diseñada para gestionar cuentas bancarias, realizar predicciones financieras y ofrecer soporte con un asistente virtual basado en IA. Desarrollado con Flask, SQLite y scikit-learn, combina tecnologías modernas para brindar una experiencia bancaria eficiente, segura e intuitiva.

Codigo Html:
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>BAM Online</title>
    <!-- Vinculación del archivo CSS -->
    <link rel="stylesheet" href="{{ url_for('static', filename='css/styles.css') }}">
</head>
<body>
    <header>
        <nav class="navbar">
            <div class="logo">
                <h1>BAM Online</h1>
            </div>
            <ul class="nav-links">
                <li><a href="{{ url_for('home') }}">Inicio</a></li>
                <li><a href="#">Cuentas</a></li>
                <li><a href="#">Transacciones</a></li>
                <li><a href="#">Préstamos</a></li>
                <li><a href="#">Contacto</a></li>
                <li><a href="#" class="btn">Cerrar Sesión</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <section class="banner">
            <h2>Bienvenido a BAM Online</h2>
            <p>Accede a tus cuentas, realiza transacciones y más desde la comodidad de tu hogar.</p>
        </section>

        <!-- Sección de Cuentas -->
        <section class="account-section">
            <h2>Resumen de tus productos</h2>
            <div class="account-info">
                <div class="account-card">
                    <h3>Monetaria Planilla</h3>
                    <p>35-1186351-6</p>
                    <p>Cachupé Santos Mario Alexander</p>
                    <p>Saldo: <span class="saldo">Q 134562.75</span></p>
                    <button class="btn">Ver Detalles</button>
                </div>
                <div class="account-card">
                    <h3>Ahorro Plus ISM</h3>
                    <p>40-5693765-5</p>
                    <p>Cachupé Santos Mario Alexander</p>
                    <p>Saldo: <span class="saldo">Q 5900.37</span></p>
                    <button class="btn">Ver Detalles</button>
                </div>
            </div>
        </section>

        <!-- Sección de Acciones Rápidas -->
        <section class="actions-section">
            <h2>Acciones Rápidas</h2>
            <div class="actions-grid">
                <div class="action-card">
                    <h3>Transferencia</h3>
                    <a href="{{ url_for('transferencia') }}" class="btn">Iniciar</a>
                </div>
                <div class="action-card">
                    <h3>Pagar Servicios</h3>
                    <a href="{{ url_for('pagar_servicios') }}" class="btn">Iniciar</a>
                </div>
                <div class="action-card">
                    <h3>Solicitar Préstamo</h3>
                    <a href="{{ url_for('solicitar_prestamo') }}" class="btn">Iniciar</a>
                </div>
                <div class="action-card">
                    <h3>Historial de Transacciones</h3>
                    <a href="{{ url_for('historial') }}" class="btn">Ver</a>
                </div>
            </div>
        </section>
    </main>

    <!-- Chatbot UI -->
    <div class="chatbot-container">
        <div class="chatbot-header">Asistente Virtual</div>
        <div class="chatbot-body" id="chatbot-body">
            <!-- Aquí se agregarán los mensajes del usuario y del bot -->
        </div>
        <div class="chatbot-input">
            <input type="text" id="chatbot-input" placeholder="Escribe tu pregunta...">
            <button onclick="enviarMensaje()">Enviar</button>
        </div>
    </div>

    <footer class="footer">
        <p>&copy; 2024 BAM Online - Todos los derechos reservados</p>
    </footer>
</body>
</html>

Codigo CSS:
/* Estilos para la barra de navegación */
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #ffffff;
    padding: 10px 20px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
.logo h1 {
    color: #003366;
    font-size: 24px;
}
.nav-links {
    list-style: none;
    display: flex;
    gap: 20px;
}
.nav-links a {
    color: #003366;
    text-decoration: none;
    font-size: 16px;
}
.nav-links .btn {
    background-color: #FF5722;
    padding: 8px 16px;
    border-radius: 5px;
    color: white;
    text-decoration: none;
}

/* Estilos generales */
body {
    background-color: #f9f9f9;
    font-family: Arial, sans-serif;
}

.banner {
    text-align: left;
    padding: 30px 20px;
    background-color: #ffffff;
    border-bottom: 2px solid #e0e0e0;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
}

.banner h2 {
    color: #003366;
    font-size: 22px;
}

.banner p {
    color: #666666;
    font-size: 14px;
}

/* Sección de cuentas */
.account-section, .actions-section {
    padding: 20px;
    text-align: left;
    background-color: #ffffff;
    margin-bottom: 20px;
}

.account-section h2 {
    font-size: 18px;
    color: #333;
    margin-bottom: 10px;
}

.account-info {
    border: 1px solid #e0e0e0;
    padding: 10px;
    border-radius: 8px;
}

.account-card {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    margin-bottom: 10px;
}

.account-card h3 {
    font-size: 16px;
    color: #333;
}

.account-card .saldo {
    font-size: 16px;
    font-weight: bold;
    color: #003366;
}

.account-card button {
    background-color: #FF5722;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

/* Sección de Acciones */
.actions-section h2 {
    font-size: 18px;
    color: #333;
    margin-bottom: 10px;
}

.actions-grid {
    display: flex;
    justify-content: space-between;
    gap: 10px;
}

.action-card {
    flex: 1;
    background-color: #f9f9f9;
    padding: 20px;
    text-align: center;
    border-radius: 10px;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
}

.action-card h3 {
    font-size: 16px;
    margin-bottom: 10px;
    color: #333;
}

.action-card .btn {
    background-color: #003366;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.action-card:hover {
    transform: scale(1.05);
}

/* Estilos del chatbot */
.chatbot-container {
    position: fixed;
    bottom: 20px;
    right: 20px;
    width: 320px;
    max-height: 520px;
    background-color: white;
    border: 1px solid #ccc;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border-radius: 12px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
}

.chatbot-header {
    background-color: #003366;
    color: #ffffff;
    padding: 12px;
    text-align: center;
    font-weight: bold;
}

.chatbot-body {
    flex: 1;
    padding: 10px;
    overflow-y: auto;
}

.chatbot-input {
    display: flex;
    padding: 10px;
    border-top: 1px solid #ccc;
}

.chatbot-input input {
    flex: 1;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.chatbot-input button {
    padding: 8px 12px;
    background-color: #003366;
    color: white;
    border: none;
    border-radius: 5px;
    margin-left: 10px;
}

.footer {
    text-align: center;
    padding: 10px 0;
    font-size: 12px;
    color: #777;
}

Codigo Python:
from flask import Flask, request, jsonify, render_template
import sqlite3
import pandas as pd
from sklearn.linear_model import LinearRegression
import numpy as np
import openai
import os

# Inicializar Flask
app = Flask(__name__)

# Configuración de OpenAI
openai.api_key = os.getenv('OPENAI_API_KEY')  # Usa una variable de entorno para mayor seguridad

# Base de datos SQLite
DATABASE = './Finanzas_db.db'

# Modelo de Regresión Lineal
regression_model = None

# Función para cargar datos CSV y entrenar el modelo de Regresión Lineal
def cargar_modelo_regresion():
    global regression_model
    try:
        # Lee los datos del archivo CSV
        data = pd.read_csv('./advertising.csv')  # Ruta del archivo CSV
        if 'radio' in data.columns and 'sales' in data.columns:
            X = data['radio'].values.reshape(-1, 1)  # Entrada: Gasto en radio
            y = data['sales'].values  # Salida: Ventas
            regression_model = LinearRegression().fit(X, y)  # Entrenar el modelo
            print("Modelo de Regresión Lineal entrenado.")
        else:
            print("No se encontraron las columnas necesarias en el CSV.")
    except Exception as e:
        print(f"Error al cargar los datos del CSV: {e}")

# Predicción con Regresión Lineal
def predecir_regresion(radio_expense):
    if not regression_model:
        raise ValueError("El modelo de Regresión Lineal no está entrenado.")
    return regression_model.predict(np.array([[radio_expense]]))[0]

# Rutas del Frontend
@app.route('/')
def home():
    return render_template('index.html')

@app.route('/transferencia')
def transferencia():
    return "Aquí va el formulario de Transferencias."

@app.route('/pagar_servicios')
def pagar_servicios():
    return "Aquí va el formulario de Pago de Servicios."

@app.route('/solicitar_prestamo')
def solicitar_prestamo():
    return "Aquí va el formulario de Solicitud de Préstamo."

@app.route('/historial')
def historial():
    return "Aquí va el historial de transacciones."

# Rutas del Backend
@app.route('/predict-regression', methods=['POST'])
def predict_regression():
    try:
        data = request.get_json()
        radio_expense = float(data.get('radioExpense', 0))
        prediction = predecir_regresion(radio_expense)
        return jsonify({'radioExpense': radio_expense, 'predictedSales': prediction})
    except Exception as e:
        return jsonify({'error': str(e)}), 500

@app.route('/chatbot', methods=['POST'])
def chatbot():
    try:
        data = request.get_json()
        pregunta = data.get('pregunta', '')
        response = openai.Completion.create(
            model="text-davinci-003",
            prompt=pregunta,
            max_tokens=150
        )
        return jsonify({'respuesta': response.choices[0].text.strip()})
    except Exception as e:
        return jsonify({'error': str(e)}), 500

@app.route('/consultarSaldo/<email>', methods=['GET'])
def consultar_saldo(email):
    try:
        conn = sqlite3.connect(DATABASE)  # Conexión a Finanzas_db
        cursor = conn.cursor()
        cursor.execute("""
            SELECT c.saldo
            FROM cuentas c
            JOIN clientes cl ON cl.id = c.id_cliente
            WHERE cl.email = ?
        """, (email,))
        row = cursor.fetchone()
        conn.close()
        if row:
            return jsonify({'saldo': f"El saldo del cliente con email {email} es: Q{row[0]}"}), 200
        else:
            return jsonify({'error': "No se encontró ninguna cuenta asociada al cliente."}), 404
    except Exception as e:
        return jsonify({'error': str(e)}), 500

# Cargar modelos al iniciar el servidor
if __name__ == '__main__':
    cargar_modelo_regresion()
    app.run(debug=True)

Codigo SQL:
-- Crear la base de datos y seleccionarla
CREATE DATABASE IF NOT EXISTS finanzas_db;
USE finanzas_db;

-- Crear la tabla usuarios
CREATE TABLE IF NOT EXISTS usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    apellido VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    fecha_registro DATE NOT NULL,
    direccion VARCHAR(255),
    telefono VARCHAR(50)
) ENGINE=InnoDB;

-- Crear la tabla transacciones
CREATE TABLE IF NOT EXISTS transacciones (
    id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT NOT NULL,
    monto DECIMAL(10, 2) NOT NULL,
    tipo ENUM('Ingreso', 'Gasto') NOT NULL,
    descripcion VARCHAR(255),
    fecha DATE NOT NULL,
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id) 
        ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB;

-- Eliminar datos previos (opcional, si estás probando)
DELETE FROM transacciones;
DELETE FROM usuarios;
ALTER TABLE transacciones AUTO_INCREMENT = 1;
ALTER TABLE usuarios AUTO_INCREMENT = 1;

-- Insertar datos en la tabla usuarios
INSERT INTO usuarios (nombre, apellido, email, fecha_registro, direccion, telefono) VALUES
('Luis', 'García', 'luis.garcia@ejemplo.com', '2023-01-01', 'Calle 1, Ciudad', '555-1234'),
('María', 'López', 'maria.lopez@ejemplo.com', '2023-02-15', 'Avenida 2, Ciudad', '555-5678'),
('Pedro', 'Martínez', 'pedro.martinez@ejemplo.com', '2023-03-10', 'Calle 3, Ciudad', '555-9101'),
('Lucía', 'Hernández', 'lucia.hernandez@ejemplo.com', '2023-04-05', 'Avenida 4, Ciudad', '555-1122');

-- Insertar datos en la tabla transacciones
INSERT INTO transacciones (usuario_id, monto, tipo, descripcion, fecha) VALUES
(1, 1000.00, 'Ingreso', 'Salario mensual', '2023-06-01'),
(1, -200.00, 'Gasto', 'Pago de servicios', '2023-06-05'),
(2, 1500.00, 'Ingreso', 'Venta de productos', '2023-06-10'),
(2, -300.00, 'Gasto', 'Compra de materiales', '2023-06-12'),
(3, 500.00, 'Ingreso', 'Reembolso', '2023-06-15'),
(4, -100.00, 'Gasto', 'Transporte público', '2023-06-20');
