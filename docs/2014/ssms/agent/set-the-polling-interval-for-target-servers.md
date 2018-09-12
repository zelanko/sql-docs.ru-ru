---
title: Установка интервала опроса на целевых серверах | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcc9d3cbdb349a60536c9a31228657e32017d903
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820160"
---
# <a name="set-the-polling-interval-for-target-servers"></a>Установка интервала опроса на целевых серверах
  В этом разделе описывается установка частоты, с которой агент [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновляет данные с главного сервера на целевых серверах. Задание — это указанная последовательность действий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Многосерверное задание — это задание, которое главный сервер выполняет на одном или нескольких целевых серверах.  
  
-   **Перед началом работы:**  [безопасность](#Security)  
  
-   **Чтобы задать интервал опроса на целевых серверах с помощью:**[SQL Server Management Studio](#SSMS), [Transact-SQL  ](#TSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 На каждом целевом сервере может одновременно выполняться только один экземпляр одного и того же задания. Каждый целевой сервер периодически опрашивает главный сервер, загружает копию новых назначенных ему заданий и отключается. Целевой сервер выполняет задание локально, а затем снова подключается к главному серверу, чтобы передать результирующее состояние задания.  
  
> [!NOTE]  
>  Если главный сервер недоступен в момент, когда целевой сервер пытается передать состояние задания, то сведения о состоянии задания помещаются в очередь, пока главный сервер не станет доступен.  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделах [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) и [Выбор правильной учетной записи службы агента SQL Server для многосерверной среды](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
 **Установка интервала опроса на целевых серверах**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  На вкладке **Состояние целевого сервера** выберите **Разместить инструкции**.  
  
4.  В списке **Тип инструкции** выберите **Установить интервал опроса**.  
  
5.  В диалоговом окне **Интервал опроса** введите количество секунд от 10 до 28 800, которое должно пройти до того, как целевой сервер начнет опрос главного сервера.  
  
6.  В пункте **Адресаты**выполните одно из следующих действий:  
  
    1.  Выберите пункт **Все целевые серверы** , если они имеют общий интервал опроса.  
  
    2.  Выберите пункт **Эти целевые серверы** , если не все серверы имеют общий интервал опроса, и выберите каждый целевой сервер, который будет использовать указанный интервал.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
 **Установка интервала опроса на целевых серверах**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса используйте [sp_post_msx_operation &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) системную хранимую процедуру, чтобы задать интервал опроса на целевых серверах.  
  
## <a name="see-also"></a>См. также  
 [dbo.sysdownloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
