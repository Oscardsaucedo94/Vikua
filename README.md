CREATE TABLE "Usuario" (
  "Id" integer NOT NULL PRIMARY KEY AUTOINCREMENT,
  "Nombre" text(20,0) NOT NULL,
  "Password" text(20,0) NOT NULL);

CREATE TABLE "Tarea" (
  "Titulo" integer NOT NULL PRIMARY KEY AUTOINCREMENT,
  "Descripcion" integer NOT NULL DEFAULT 0,
  "Tipo" boolean NOT NULL DEFAULT 0);

CREATE TABLE "Prioridad" (
  "Id" integer NOT NULL PRIMARY KEY AUTOINCREMENT,
  "Name" text(20,0) NOT NULL);
---------------------------------------------
private RemoteDataAdapter dataAdapter;
private DataTable tasksTable;
private DataTable prioritiesTable;
private DataTableModel tasksTableModel;
private DataTableModel prioritiesTableModel;

public DataModule() {
    initComponents();
    initTables();
}

private void initTables() {
    this.tasksTable = new DataTable("Tasks");
    this.tasksTableModel = new DataTableModel(this.tasksTable);
    this.tasksTable.addTableDataChangedListener(tasksTableModel);
    
    this.prioritiesTable = new DataTable("Priorities");
    this.prioritiesTableModel = new DataTableModel(this.prioritiesTable);
    this.prioritiesTable.addTableDataChangedListener(this.prioritiesTableModel);            
}

public DataTableModel getTasksDataTableModel() {
    return tasksTableModel;
}
