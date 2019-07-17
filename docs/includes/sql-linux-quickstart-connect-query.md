---
ms.openlocfilehash: 549224ae30b710292324a178aa48432bde7d34ca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215638"
---
## <a name="connect-locally"></a>Локальное подключение

В следующих шагах выполняется локальное подключение к новому экземпляру SQL Server с помощью **sqlcmd**.

1. Запустите **sqlcmd** с параметрами имени вашего SQL Server (-S), имени пользователя (-U) и пароля (-P). В этом руководстве вы подключаетесь локально, поэтому имя сервера — `localhost`. Имя пользователя — `SA`, а пароль тот, что вы выбрали для учетной записи SA во время установки.

   ```bash
   sqlcmd -S localhost -U SA -P '<YourPassword>'
   ```

   > [!TIP]
   > Вы можете не указывать пароль в командной строке. В этом случае вы получите запрос на его ввод.

   > [!TIP]
   > Если вы в будущем захотите подключиться удаленно, укажите для параметра **-S** имя компьютера или IP-адрес и откройте в брандмауэре порт 1433.

1. Если все сработает должным образом, вы перейдете к приглашению команды **sqlcmd**: `1>`.

1. Если произойдет сбой подключения, сначала попробуйте узнать проблему по сообщению об ошибке. Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением](../linux/sql-server-linux-troubleshooting-guide.md#connection).

## <a name="create-and-query-data"></a>Создание и запрос данных
В следующих разделах приведено пошаговое руководство по созданию базы данных, добавлению данных и запуску простого запроса с использованием **sqlcmd**.

### <a name="create-a-new-database"></a>Создание базы данных

Выполните следующие шаги, чтобы создать базу данных `TestDB`.

1. В приглашении команды **sqlcmd** вставьте следующую команду Transact-SQL, чтобы создать тестовую базу данных:

   ```sql
   CREATE DATABASE TestDB
   ```

1. В следующей строке напишите запрос, который должен вернуть имена всех баз данных на сервере:

   ```sql
   SELECT Name from sys.Databases
   ```

1. Две предыдущие команды были выполнены не сразу. Необходимо ввести `GO` на новой строке, чтобы выполнить предыдущие команды:

   ```sql
   GO
   ```

> [!TIP]
> Дополнительные сведения о написании инструкций Transact-SQL и запросов, см. в разделе [руководства: Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md).

### <a name="insert-data"></a>Вставка данных

Теперь создайте таблицу `Inventory` и вставьте две новых строки.

1. В приглашении команды **sqlcmd** переключите контекст на новую базу данных `TestDB`:

   ```sql
   USE TestDB
   ```

1. Создайте таблицу `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Вставьте данные в новую таблицу:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Введите `GO`, чтобы выполнить предыдущие команды:

   ```sql
   GO
   ```

### <a name="select-data"></a>Выбор данных

Теперь выполните запрос, чтобы вернуть данные из таблицы `Inventory`.

1. В приглашении команды **sqlcmd** введите запрос, который должен вернуть из таблицы `Inventory` строки, где количество превышает 152:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Выполните команду:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Выход из приглашения команды sqlcmd

Чтобы завершить сеанс **sqlcmd**, введите `QUIT`:

```sql
QUIT
```

## <a name="performance-best-practices"></a>Рекомендации по повышению производительности

После установки SQL Server в Linux, советы и рекомендации по настройке, Linux и SQL Server для повышения производительности для рабочих сценариев. Дополнительные сведения см. в разделе [рекомендации по производительности и рекомендации по конфигурации для SQL Server в Linux](../linux/sql-server-linux-performance-best-practices.md).

## <a name="cross-platform-data-tools"></a>Данные кросс платформенные средства

В дополнение к **sqlcmd**, можно использовать следующие кросс платформенные средства для управления SQL Server:

|||
|---|---|
| [Azure Data Studio](../azure-data-studio/index.md) | Кросс платформенных графического интерфейса пользователя базы данных управления служебной программы. |
| [Visual Studio Code](../linux/sql-server-linux-develop-use-vscode.md); | Редактор кода графического пользовательского интерфейса между различными платформами, выполните инструкции Transact-SQL с помощью расширения mssql. |
| [PowerShell Core](../linux/sql-server-linux-manage-powershell-core.md) | Кросс платформенные службы автоматизации и настройки tool на основе командлетов. |
| [mssql-cli](https://github.com/dbcli/mssql-cli/tree/master/doc) | Кросс платформенного интерфейса командной строки для выполнения команд Transact-SQL. |

## <a name="connecting-from-windows"></a>Подключение из Windows

Инструменты SQL Server в Windows подключаются к экземплярам SQL Server в Linux так же, как они подключались бы к любому удаленному экземпляру SQL Server.

Если у вас компьютер с ОС Windows, который может подключаться к компьютеру с ОС Linux, попробуйте выполнить те же действия этого раздела в командной строке Windows, запустив **sqlcmd**. Главное при этом — использовать имя или IP-адрес целевого компьютера с ОС Linux, а не localhost, и открыть TCP-порт 1433. Если у вас возникли проблемы с подключением из Windows, см. [рекомендации по устранению неполадок с подключением](../linux/sql-server-linux-troubleshooting-guide.md#connection).

Другие инструменты, которые запускаются в Windows, но подключаются к SQL Server на Linux:

- [SQL Server Management Studio (SSMS)](../linux/sql-server-linux-manage-ssms.md)
- [Windows PowerShell](../linux/sql-server-linux-manage-powershell.md)
- [SQL Server Data Tools (SSDT)](../linux/sql-server-linux-develop-use-ssdt.md)

## <a name="other-deployment-scenarios"></a>Другие сценарии развертывания

По другим сценариям установки доступны следующие ресурсы.

|||
|---|---|
| [Обновление](../linux/sql-server-linux-setup.md#upgrade) | Узнайте, как обновить установленную среду SQL Server на Linux |
| [Удаление](../linux/sql-server-linux-setup.md#uninstall) | Удаление SQL Server на Linux |
| [Автоматическая установка](../linux/sql-server-linux-setup.md#unattended) | Узнайте, как создать сценарий для установки без каких-либо запросов |
| [Автономная установка](../linux/sql-server-linux-setup.md#offline) | Узнайте, как вручную загрузить пакеты для установки в автономном режиме |

> [!TIP]
> Ответы на часто задаваемые вопросы см. в разделе [SQL Server на Linux часто задаваемые вопросы о](../linux/sql-server-linux-faq.md).

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Ознакомьтесь с учебниками для SQL Server в Linux](../linux/sql-server-linux-migrate-restore-database.md)