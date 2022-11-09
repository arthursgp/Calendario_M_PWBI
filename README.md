//(DataInicial as date, DataFinal as date)=>
let
    DataInicial = #date(2010, 1, 1),
    DataFinal = #date(2030,12, 31),
    QtdeDias = Duration.Days(DataFinal - DataInicial) + 1,
    Datas = List.Dates(DataInicial, QtdeDias, #duration(1,0,0,0)),
    Cabecalho = type table[Data=date, Ano=Int32.Type, Nome do Mês=text, Mês=Int32.Type],
    Registros = List.Transform(
        Datas,
        each {
            _ ,
            Date.Year(_),
            Date.MonthName(_),
            Date.Month(_)
        }
    ),
    Tabela = #table(Cabecalho, Registros)
in
    Tabela
