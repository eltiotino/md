cd flask

cambiamos el .env
```
DEBUG=False
SECRET_KEY=S3cr3t_K#Key
DB_ENGINE=mysql
DB_NAME=bszjofg7vz5p7vhx5ce0
DB_HOST=bszjofg7vz5p7vhx5ce0-mysql.services.clever-cloud.com
DB_PORT=3306
DB_USERNAME=u0xc0e3psl5y1gt3
DB_PASS=voF8X2zIC8KHoiFOmWut
```


> pip install -r requirements.txt

lo dejamos iguak

instalamos pymysql
> pip install pymysql

modificamos el fichero __run__.py
```

DEBUG=True

if DEBUG:
    app.logger.info('DEBUG       = ' + str(DEBUG)      )
    print (DEBUG)
    app.logger.info('Environment = ' + get_config_mode )
    print ( get_config_mode)
    app.logger.info('DBMS        = ' + app_config.SQLALCHEMY_DATABASE_URI )
    print(app_config.SQLALCHEMY_DATABASE_URI)
else :
    print (DEBUG)
    print ( get_config_mode)
    print(app_config.SQLALCHEMY_DATABASE_URI)
    print('mal')
````

ahora modificamos el config.py

```
# This will create a file in <app> FOLDER
    #SQLALCHEMY_DATABASE_URI = 'sqlite:///' + os.path.join(basedir, 'db.sqlite3')
    SQLALCHEMY_DATABASE_URI = 'mysql+pymysql://b0bb873fa494ef:2348f559@eu-cdbr-west-01.cleardb.com/heroku_d0760f9ea4b61ba'
```
y por ultimo el models-py en el directorio /app/base

```
class User(db.Model, UserMixin):

    __tablename__ = 'User'

    id = Column(Integer, primary_key=True)
    username = Column(String(50), unique=True)
    email = Column(String(50), unique=True)
    password = Column(Binary)

    def __init__(self, **kwargs):
        for property, value in kwargs.items():
            # depending on whether value is an iterable or not, we must
            # unpack it's value (when **kwargs is request.form, some values
            # will be a 1-element list)
            if hasattr(value, '__iter__') and not isinstance(value, str):
                # the ,= unpack of a singleton fails PEP8 (travis flake8 test)
                value = value[0]

            if property == 'password':
                value = hash_pass( value ) # we need bytes here (not plain str)
                
            setattr(self, property, value)

    def __repr__(self):
        return str(self.username)

```

eso es todo
