# mapping
Type Mapping for different sources data DB, Forms, API

## How it works

Zasada działania polega na mapowaniu typów danych i procesów z różnych źródeł danych

Mapowanie procesów jest przeprowadzane do postcaci CRUD
W przypadku bazy danych Crud będzie przeprowadzane na każdym typie danych:
Column, Row, Table, Database

    class Source
        type: Mysql
        handle: 
        
    class Param
        type: String
        name: Username
        path: User
        id: 2
        source: Mysql
                        
        
        
Polega to na definicji źródła, np 
    
    new Source(new Mysql);
    
    new Source(new Post);
    
    new ParamCollection();
        add(new Param(new Type\String(), 'Username', 'User', 2));
        add(new Param(new Type\String(), 'Password', 'User', 2));
       
    
Wykonaniu prcoesu na parametrze zlokalizowanych w źródle, np 
zapisanie zmiennych z metody POST i zapisanie do Bazy danych: 
    
    new Process(new \Crud\Read());
        new Run(new Process(), new ParamCollection(), new Source(new Post));
        
    new Process(new \Crud\Create());
        new Run(new Process(), new ParamCollection(), new Source(new Mysql));

Do każdego źródła trzeba zdefiniować Liste Parametrów