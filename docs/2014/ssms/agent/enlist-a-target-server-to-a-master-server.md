---
title: Добавление целевого сервера к главному | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f3d0d91de95e82fcd174aa9290e208afda5bef91
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52786216"
---
# <a name="enlist-a-target-server-to-a-master-server"></a>Прикрепление целевого сервера к главному
  В этом разделе описывается, как добавить целевые серверы в конфигурацию администрирования нескольких серверов. Запустите эту процедуру с главного сервера. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server (SMO).  
  
 Дополнительные сведения о влиянии учетной записи Windows для службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на многосерверную среду см. в разделе [Создание многосерверной среды](create-a-multiserver-environment.md).  
  
 По умолчанию полное шифрование SSL и проверка сертификата включены для соединений между главными и целевыми серверами. Дополнительные сведения см. в статье [Установка параметров шифрования на целевых серверах](set-encryption-options-on-target-servers.md).  
  
 **В этом разделе**  
  
-   **Для прикрепления целевого сервера используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-enlist-a-target-server"></a>Прикрепление целевого сервера  
  
1.  В **Обозревателе объектов**разверните главный сервер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Добавление целевых серверов**.  
  
3.  Завершите работу мастера настройки целевого сервера, который проводит пользователя по этапам процесса.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-enlist-a-target-server"></a>Прикрепление целевого сервера  
  
1.  Используйте хранимую процедуру `sp_msx_enlist`.  Дополнительные сведения см. в разделе [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
##  <a name="PowerShellProcedure"></a> Использование управляющих объектов SQL Server (SMO)  
  
## <a name="see-also"></a>См. также  
 [Автоматизация администрирования в масштабах предприятия](automated-administration-across-an-enterprise.md)  
  
  
