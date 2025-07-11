
Guardado y cargado en JSON:

usando la libreria "gson", implementé los metodos "guardarEnJSON(String path)" y "cargarDesdeJSON(String path)" para guardar en un archivo .json, y poder leer los datos de un archivo .json.

Para esto tuve que hacer un LocalDateAdapter, ubicado en la carpeta "config", ya que no podía convertir naturalemte el tipo de dato LocalDate del atributo fecha. Lugo se lo pasé al gson en ambas funciones con el metodo "registerTypeAdapter()".

Además utilicé tanto el JsonWriter como el JsonReader para guardar y leer datos. Para esto precise crear un JsonElement en "guardarEnJSON()" para no generar un TypeToken a la hora de usar el JsonWriter, pero para el "gson.fromJson()" si tuve que usar un objeto Type con el tipo de dato que usara para interpretar lo que recibe.

Para probar ambas funciones utilicé esto:

gestor.guardarEnJSON(AppConfig.PATH_JSON.toString());
GestorEventos<EventoMusical> gestorJSON= new GestorEventos<>();
gestorJSON.cargarDesdeJSON(AppConfig.PATH_JSON.toString());
System.out.println("\nEventos cargados desde archivo JSON:");
gestorJSON.mostrarTodos();