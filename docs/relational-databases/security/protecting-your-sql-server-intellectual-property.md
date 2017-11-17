---
title: "Защита интеллектуальной собственности SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 01/31/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protecting intellectual property
- intellectual property
ms.assetid: 174a646a-d65c-4074-8249-d783e91be2dd
caps.latest.revision: 3
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 7b4f037616e0559ac62bbae5dbe04aeffe529b06
ms.openlocfilehash: 36377fe5db9440651b4e63a2c848efc290470d3e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="protecting-your-sql-server-intellectual-property"></a>Защита интеллектуальной собственности SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Разработчики программного обеспечения часто спрашивают, каким образом можно распространить приложение данных [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] среди заказчиков и при этом предотвратить возможность его анализа и разборки. Ключевым аргументом в данном случае является защита интеллектуальной собственности, которая обеспечивается лицензионным соглашением. Когда [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] устанавливается на компьютер, доступ к которому имеется у других администраторов, вы теряете некоторый контроль над этой собственностью. 

## <a name="nature-of-the-problem"></a>Суть проблемы
У владельца или администратора компьютера всегда есть доступ к экземпляру [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], установленному на этом компьютере. Когда вы развертываете приложение на компьютере заказчика, он как администратор может подключиться к [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] в качестве участника предопределенной роли сервера **sysadmin**. Эта роль включает возможность предоставления разрешений, управления резервным копированием (включая восстановление резервных копий на других компьютерах), расшифровки, перемещения файлов данных и т. д. Дополнительные сведения см. в статье [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md). 

Хранимые процедуры и данные можно зашифровать, но скрыть структуру данных невозможно, и пользователи, у которых есть право на подключение отладчика к серверному процессу, могут получить расшифрованные процедуры и данные из памяти во время выполнения.

Если клиенты не являются администраторами компьютеров, вы можете ограничить их доступ. Вы можете зашифровать резервные копии и файлы данных с помощью [прозрачного шифрования данных](../../relational-databases/security/encryption/transparent-data-encryption.md), а также производить аудит действий всех пользователей. Но администраторы [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и администраторы компьютера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] могут отклонить эти действия.

## <a name="solution"></a>Решение
Есть разные способы настройки клиентского доступа к данным без установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] на компьютерах клиентов. Самым простым способом является, вероятно, использование [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], где у клиентов нет роли администратора, а также [постоянного шифрования](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Дополнительные сведения об основах работы с [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] см. в статье [Что такое база данных SQL? Введение в базу данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview).  

Вы также можете разместить [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] в собственной сети и разрешить клиентам доступ к данным через сеть, напрямую или через веб-приложение.

## <a name="see-also"></a>См. также:

[Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
[Обеспечение безопасности SQL Server](../../relational-databases/security/securing-sql-server.md)  


