# Filtrar los albaranes a firmar de la app por el agente asociado al usuario conectado


### Webapp / Filtro en albaranes
Añadiremos a la pantalla un filtro que funcionará de la siguiente forma:
+ Si el usuario conectado está marcado en la tabla de usuarios como Superusuario, verá todos los albaranes.
+ Si el usuario conectado no está marcado como Superusuario:
    + Si existe un único agente comercial ligado al usuario (pantalla de Agentes, campo Usuario), mostrará los albaranes cuyo agente comercial corresponda con el agente del usuario.
    + Si no existe o hay más de un agente comercial ligado al usuario (pantalla de Agentes, campo Usuario), la aplicación no mostrará ningún dato, indicando el mensaje:

        _El usuario X no está ligado a un único agente comercial. Puede hacer la asociación en el formulario de Agentes del ERP_
