## Configuracion e instalacion en linux mind -- (x Benjamin Baigorria --)
1. Actualizar el sistema


```bash
# (Verificacion de paquetes)
# (Actualizacion de paquetes)
sudo apt update  
sudo apt upgrade 
```

2. Instalacion de PSQL

```bash
sudo apt install postgresql postgresql-contrib
```

3. Verificacion de la instalacion

```bash
sudo systemctl status postgresql
```

4. Configuracion Basica PostgreSQL

Acceder a PostgreSQL

```bash
# Cambiar al usuario postgres
sudo -u postgres psql
```

5. Crear usuario y contraseña

```bash
CREATE USER mi_usuario WITH PASSWORD 'tu_password';
CREATE DATABASE mi_base_de_datos OWNER mi_usuario;
GRANT ALL PRIVILEGES ON DATABASE mi_base_de_datos TO mi_usuario;
\q
```

6. Configurar el acceso remoto (opcional)

```bash
sudo nano /etc/postgresql/16/main/postgresql.conf
```

Buscar en el documento : listen_addresses = 'localhost'
Cambiarlo 'localhost' por '*' 
Esto acta coneciones desde diversas IPs (Revisar para confirmar)

7. Editar archivo de autenticacion

```bash
sudo nano /etc/postgresql/16/main/pg_hba.conf
```
Agregar al final del archivo :

host    all             all             0.0.0.0/0               md5

8. Reiniciar el servicio

```bash
sudo systemctl restart postgresql
```

9. Instalar gestor grafico


10. Comandos utiles

```bash
# Iniciar servicio
sudo systemctl start postgresql

# Detener servicio
sudo systemctl stop postgresql

# Reiniciar servicio
sudo systemctl restart postgresql

# Ver estado
sudo systemctl status postgresql
```

11. Conexion con la base de datos

```bash
# Conectar como usuario específico
psql -U mi_usuario -d mi_base_de_datos -h localhost

# Conectar como postgres
sudo -u postgres psql
```

12. Verificacion

```bash
# Ver versión instalada
psql --version

# Conectar y ejecutar una consulta simple
sudo -u postgres psql -c "SELECT version();"
```