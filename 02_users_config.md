add user: para agregar ususarios en su propia bd de jeing
- Ir a menu user -> Create User

Security:
- En apartado de Authentication: 
  - Security Realm -> Jenkins' own user database
  - En Authorization -> Project-base Matrix Authorization Strategy

Para configuracion con roles se debe instalar plugin:
Role-based Authorization Strategy
- En Authorization -> Role-Bases Strategy
- Ahora en Jenkins Manager hay un nueva opcion "Manage and Assign Roles"