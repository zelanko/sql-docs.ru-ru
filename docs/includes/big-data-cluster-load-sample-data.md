### <a id="sampledata"></a> Загрузка образца данных

Учебники по кластера больших данных в SQL Server используются общие наборы данных выборки. Следуйте инструкциям ниже, чтобы настроить образец данных в кластере большие данные:

1. Если у вас нет средства командной строки SQL Server (**sqlcmd** и **bcp**), сначала установите эти средства с одной из ссылок:

   * **Windows**: [средства командной строки установки SQL Server на Windows](https://www.microsoft.com/download/details.aspx?id=53591)
   * **Linux**: [средства командной строки установки SQL Server в Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-tools)

1. Загрузить образец файла резервной копии [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) на компьютер.

1. Перейдите к кластеру больших данных SQL Server 2019 [каталог образцов](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster).

1. Скачайте [bootstrap пример db.sql](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql) сценарий Transact-SQL.

1. Скачайте и запустите один из этих двух сценариев из командной строки.

   * **Windows**: [bootstrap пример db.cmd](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd)
   * **Linux**: [bootstrap пример db.sh](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh)

   > [!TIP]
   > Инструкции по использованию можно получить, запустив сценарий без параметров.

Скрипт восстанавливает образца базы данных master экземпляра SQL Server, а также загружает данные в HDFS в пуле носителей.