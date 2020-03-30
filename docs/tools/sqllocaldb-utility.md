---
title: Программа SqlLocalDB
ms.custom: seo-lt-2019
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c829c9adce95dd1a4a84d5fd6fc7b88abdece96a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75306671"
---
# <a name="sqllocaldb-utility"></a>Программа SqlLocalDB
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Для создания экземпляра [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB** используйте служебную программу **SqlLocalDB**. Служебная программа **SqlLocalDB** (SqlLocalDB.exe) — это простая программа командной строки, с помощью которой пользователи и разработчики могут создавать экземпляры [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB** и управлять ими. Сведения об использовании **LocalDB**см. в статье [Экспресс-выпуск SQL Server 2016 LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] \<instance-name>  \<instance-version> [-s ]  
    | [ delete   | d ] \<instance-name>  
    | [ start    | s ] \<instance-name>  
    | [ stop     | p ] \<instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] [" <user_SID> " | " <user_account> " ] " \<private-name> " " \<shared-name> "  
    | [ unshare  | u ] " \<shared-name> "  
    | [ info     | i ] \<instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **create** | **c** ] *\<имя-экземпляра>* *\<версия-экземпляра>* [ **-s** ]  
 Создает новый экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. В **SqlLocalDB** используется версия двоичных файлов [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], указанная в аргументе *\<версия-экземпляра>* . Номер версии задается в числовом формате и содержит хотя бы один знак после разделителя. Дополнительные номера версии (пакеты обновления) являются необязательными. Например, можно указать следующие номера версий: 11.0 или 11.0.1186. Указываемая версия должна быть установлена на компьютере. Если номер версии не указан, то по умолчанию используется версия программы **SqlLocalDB** . В случае добавления параметра **-s** запускается новый экземпляр **LocalDB**.  
  
 [ **share** | **h** ]  
 Делает указанный частный экземпляр **LocalDB** общим, используя указанное общее имя. Если идентификатор безопасности пользователя или имя учетной записи не указаны, используется значение по умолчанию — имя текущего пользователя.  
  
 [ **unshared** | **u** ]  
 Отменяет общий доступ к указанному экземпляру **LocalDB**.  
  
 [ **delete** | **d** ] *\<имя-экземпляра>*  
 Удаляет указанный экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.  
  
 [ **start** | **s** ] " *\<имя-экземпляра>* "  
 Запускает указанный экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. В случае успешного завершения инструкция возвращает адрес именованного канала **LocalDB**.  
  
 [ **stop** | **p** ] *\<имя-экземпляра>* [ **-i** ] [ **-k** ]  
 Останавливает указанный экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. В случае добавления параметра **-i** запрашивается завершение работы экземпляра с параметром **NOWAIT**. В случае добавления параметра **-k** процесс экземпляра завершается без обращения к нему.  
  
 [ **info** | **i** ] [ *\<имя-экземпляра>* ]  
 Перечисляет все экземпляры [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** , принадлежащие текущему пользователю.  
  
 Параметр *\<имя-экземпляра* возвращает имя, версию, состояние ("Выполняется" или "Остановлено"), время последнего запуска для указанного экземпляра [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** и имя локального канала для **LocalDB**.  
  
 [ **trace** | **t** ] **on** | **off**  
 Параметр**trace on** включает трассировку вызовов API **SqlLocalDB** для текущего пользователя. Параметр**trace off** отключает трассировку.  
  
 **-?**  
 Возвращает краткое описание каждого параметра **SqlLocalDB** .  
  
## <a name="remarks"></a>Remarks  
 В аргументе *имя-экземпляра* должны соблюдаться правила для идентификаторов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . В противном случае он должен заключаться в двойные кавычки.  
  
 При выполнении SqlLocalDB без аргументов возвращается текст справки.  
  
 Любые операции, за исключением запуска, могут выполняться только с экземпляром, принадлежащим текущему пользователю. Экземпляр SQLLOCALDB при общем использовании может запускать и останавливать только его владелец.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-an-instance-of-localdb"></a>A. Создание экземпляра LocalDB  
 В следующем примере экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** с именем `DEPARTMENT` создается с помощью двоичных файлов [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , а затем запускается.  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a>Б. Работа с общим экземпляром LocalDB  
 Откройте командную строку с правами доступа администратора.  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 Выполните следующий код, чтобы подключиться к общему экземпляру **LocalDB** с использованием имени входа `NewLogin` .  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server 2016 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
[Программа командной строки: SqlLocalDB.exe](../relational-databases/express-localdb-instance-apis/command-line-management-tool-sqllocaldb-exe.md)  
  
