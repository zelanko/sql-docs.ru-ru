---
title: Защита интеллектуальной собственности SQL Server | Документация Майкрософт
description: Узнайте о вариантах защиты интеллектуальной собственности в распространенном между клиентами приложении для работы с данными SQL Server.
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- protecting intellectual property
- intellectual property
ms.assetid: 174a646a-d65c-4074-8249-d783e91be2dd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dc6b2c88fc2405aea99ac8ce7de9c38cf43c99aa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773881"
---
# <a name="protecting-your-sql-server-intellectual-property"></a>Защита интеллектуальной собственности SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Разработчики программного обеспечения часто спрашивают, каким образом можно распространить приложение данных [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] среди заказчиков и при этом предотвратить возможность его анализа и разборки. Ключевым аргументом в данном случае является защита интеллектуальной собственности, которая обеспечивается лицензионным соглашением. Когда [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] устанавливается на компьютер, доступ к которому имеется у других администраторов, вы теряете некоторый контроль над этой собственностью. 

## <a name="nature-of-the-problem"></a>Суть проблемы
У владельца или администратора компьютера всегда есть доступ к экземпляру [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], установленному на этом компьютере. Когда вы развертываете приложение на компьютере заказчика, он как администратор может подключиться к [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] в качестве участника предопределенной роли сервера **sysadmin**. Эта роль включает возможность предоставления разрешений, управления резервным копированием (включая восстановление резервных копий на других компьютерах), расшифровки, перемещения файлов данных и т. д. Дополнительные сведения см. в статье [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md). 

Хранимые процедуры и данные можно зашифровать, но скрыть структуру данных невозможно, и пользователи, у которых есть право на подключение отладчика к серверному процессу, могут получить расшифрованные процедуры и данные из памяти во время выполнения.

Если клиенты не являются администраторами компьютеров, вы можете ограничить их доступ. Вы можете зашифровать резервные копии и файлы данных с помощью [прозрачного шифрования данных](../../relational-databases/security/encryption/transparent-data-encryption.md), а также производить аудит действий всех пользователей. Но администраторы [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и администраторы компьютера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] могут отклонить эти действия.

## <a name="solution"></a>Решение
Есть разные способы настройки клиентского доступа к данным без установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] на компьютерах клиентов. Самым простым способом является, вероятно, использование [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], где у клиентов нет роли администратора, а также [постоянного шифрования](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Дополнительные сведения об основах работы с [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] см. в статье [Что такое база данных SQL? Введение в базу данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview).  

Вы также можете разместить [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] в собственной сети и разрешить клиентам доступ к данным через сеть, напрямую или через веб-приложение.

## <a name="see-also"></a>См. также:

[Центр безопасности для ядра СУБД SQL Server и Базы данных Azure SQL](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
[Обеспечение безопасности SQL Server](../../relational-databases/security/securing-sql-server.md)  

