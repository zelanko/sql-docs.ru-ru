---
title: Служебная программа SqlLocalDB | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f13a16e7c8f507914abe8529e02b76161072c5bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035404"
---
# <a name="sqllocaldb-utility"></a>Программа SqlLocalDB
  Используйте `SqlLocalDB` программу для создания экземпляра [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB**. `SqlLocalDB` Программа (SqlLocalDB. exe) — это простое средство командной строки, которое позволяет пользователям и разработчикам создавать и администрировать экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**. Сведения об использовании **LocalDB**см. в разделе [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **Создание** | **c** ] имя экземпляра>* \<экземпляр — версия>* [**-s** ] * \<*  
 Создает новый экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. `SqlLocalDB`использует версию [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] двоичных файлов, заданную аргументом * \<>версии экземпляра* . Номер версии задается в числовом формате и содержит хотя бы один знак после разделителя. Дополнительные номера версии (пакеты обновления) являются необязательными. Например, следующие два номера версии будут допустимыми: 11.0 и 11.0.1186. Указываемая версия должна быть установлена на компьютере. Если значение не указано, по умолчанию используется версия `SqlLocalDB` программы. В случае добавления параметра **-s** запускается новый экземпляр **LocalDB**.  
  
 [ **общий доступ** | **h** ]  
 Делает указанный частный экземпляр **LocalDB** общим, используя указанное общее имя. Если идентификатор безопасности пользователя или имя учетной записи не указаны, используется значение по умолчанию — имя текущего пользователя.  
  
 [ **несовместное использование** | **u** ]  
 Отменяет общий доступ к указанному экземпляру **LocalDB**.  
  
 [ **Delete** | **d** ] * \<имя экземпляра>*  
 Удаляет указанный экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.  
  
 [ **Начало** | **]** "*\<instance-name>*"  
 Запускает указанный экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. В случае успешного завершения инструкция возвращает адрес именованного канала **LocalDB**.  
  
 [ **останавливаться** | **p** ] имя экземпляра>[**-i** ] [**-k** ] * \<*  
 Останавливает указанный экземпляр [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**. Добавление **-i** запрашивает завершение работы экземпляра с `NOWAIT` параметром. В случае добавления параметра **-k** процесс экземпляра завершается без обращения к нему.  
  
 [ **info** | **i** ] [ * \<имя экземпляра>* ]  
 Перечисляет все экземпляры [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** , принадлежащие текущему пользователю.  
  
 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] * \<имя экземпляра>* возвращает имя, версию, состояние (запущено или остановлено), время последнего запуска для указанного экземпляра **LocalDB**и имя локального канала **LocalDB**.  
  
 [ **Трассировка** | **t** ]  | **выключено** ****  
 **Trace on** включает трассировку вызовов `SqlLocalDB` API для текущего пользователя. **Трассировка отключена** отключает трассировку.  
  
 **-?**  
 Возвращает краткое описание каждого `SqlLocalDB` параметра.  
  
## <a name="remarks"></a>Remarks  
 В аргументе *имя-экземпляра* должны соблюдаться правила для идентификаторов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . В противном случае он должен заключаться в двойные кавычки.  
  
 При выполнении SqlLocalDB без аргументов возвращается текст справки.  
  
 Любые операции, за исключением запуска, могут выполняться только с экземпляром, принадлежащим текущему пользователю.  
  
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
 [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
