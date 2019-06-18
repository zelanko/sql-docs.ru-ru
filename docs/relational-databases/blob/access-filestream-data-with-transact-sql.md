---
title: Доступ к данным FILESTREAM с помощью Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Transact-SQL
ms.assetid: a6bf0ce7-7e5e-4a07-8917-ee526c9d0a05
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32b9fbb1967c3d98ccc6dbb149bea40da735c887
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089056"
---
# <a name="access-filestream-data-with-transact-sql"></a>Доступ к данным FILESTREAM с помощью Transact-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описаны способы использования инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE и DELETE для управления данными FILESTREAM.  
  
> [!NOTE]  
>  Для примеров в этом разделе требуется база данных с поддержкой FILESTREAM и таблица, которая создана в разделе [Создание базы данных с поддержкой FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md) и [Создание таблицы для хранения данных FILESTREAM](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md).  
  
##  <a name="ins"></a> Вставка строки, содержащей данные FILESTREAM  
 Чтобы вставить строку в таблицу, которая поддерживает данные FILESTREAM, используйте инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT. Значение, вставляемое в столбец FILESTREAM, может быть либо значением NULL, либо значением типа **varbinary(max)** .  
  
### <a name="inserting-null"></a>Вставка значения NULL  
 Следующий пример иллюстрирует порядок вставки значения `NULL`. Если значение FILESTREAM равно `NULL`, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не создает файл в файловой системе.  
  
 [!code-sql[FILESTREAM#FS_InsertNULL](../../relational-databases/blob/codesnippet/tsql/access-filestream-data-w_1_1.sql)]  
  
### <a name="inserting-a-zero-length-record"></a>Вставка записи с нулевой длиной  
 В следующем примере показано, как использовать инструкцию `INSERT` для создания записи с нулевой длиной. Это бывает полезно в случае, если нужно получить дескриптор файла, работать с которым предполагается с помощью API-интерфейсов Win32.  
  
 [!code-sql[FILESTREAM#FS_InsertZero](../../relational-databases/blob/codesnippet/tsql/access-filestream-data-w_1_2.sql)]  
  
### <a name="creating-a-data-file"></a>Создание файла данных  
 В следующем примере кода показывается, как использовать инструкцию `INSERT` для создания файла, содержащего данные. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] преобразует строку `Seismic Data` в значение типа `varbinary(max)` . FILESTREAM создает файл Windows, если он еще не был создан. Затем данные добавляются в файл данных.  
  
 [!code-sql[FILESTREAM#FS_InsertData](../../relational-databases/blob/codesnippet/tsql/access-filestream-data-w_1_3.sql)]  
  
 При выборе всех данных в таблице `Archive.dbo.Records` результат напоминает тот, который приведен в следующей таблице. Однако столбец `Id` будет содержать разные идентификаторы GUID.  
  
|Идентификатор|SerialNumber|Диаграмма|  
|--------|------------------|------------|  
|`C871B90F-D25E-47B3-A560-7CC0CA405DAC`|`1`|`NULL`|  
|`F8F5C314-0559-4927-8FA9-1535EE0BDF50`|`2`|`0x`|  
|`7F680840-B7A4-45D4-8CD5-527C44D35B3F`|`3`|`0x536569736D69632044617461`|  
  
  
##  <a name="upd"></a> Обновление данных FILESTREAM  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать для обновления данных файла, хотя это может быть нежелательным при потоковой записи в файл больших объемов данных.  
  
 В следующем примере любой текст в записи файла заменяется текстом `Xray 1`.  
  
 [!code-sql[FILESTREAM#FS_UpdateData](../../relational-databases/blob/codesnippet/tsql/access-filestream-data-w_1_4.sql)]  
  
  
##  <a name="del"></a> Удаление данных FILESTREAM  
 При удалении строки, содержащей поле FILESTREAM, также удаляются и связанные с ней файлы файловой системы. Единственным способом удаления строки и, как следствие, файла является использование инструкции DELETE языка [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 В следующем примере показано, как удалить строку и связанный с ней файл файловой системы.  
  
 [!code-sql[FILESTREAM#FS_DeleteData](../../relational-databases/blob/codesnippet/tsql/access-filestream-data-w_1_5.sql)]  
  
 При выборе всех данных в таблице `Archive.dbo.Records` строка удаляется, и связанный с ней файл больше нельзя использовать.  
  
> [!NOTE]  
>  Базовые файлы удаляются сборщиком мусора FILESTREAM.  
  
  
## <a name="see-also"></a>См. также:  
 [Включение и настройка FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [Избегание конфликтов в операциях баз данных в приложениях FILESTREAM](../../relational-databases/blob/avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
