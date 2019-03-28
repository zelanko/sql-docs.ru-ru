---
title: Как подготовить SQL Server для CDC | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a327fa18-58f4-4e69-bb87-44faf47e20ef
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5f0d535dbd5c451a88541dfc3432b9b09a7f6194
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275843"
---
# <a name="how-to-prepare-sql-server-for-cdc"></a>Как подготовить SQL Server для CDC
  Для службы Oracle CDC требуется, чтобы все целевые экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержали базу данных MSXDBCDC. Эта база данных создается с помощью операции «Подготовка SQL Server» в консоли конфигурации служб CDC. Это действие выполняется только один раз для каждого целевого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Ниже описана подготовка базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для службы системы отслеживания измененных данных Oracle при помощи консоли конфигурации службы CDC. Этот процесс создает базу данных MSXDBCDC и определяет необходимые таблицы, хранимые процедуры и другие требуемые артефакты.  
  
 Подготовка SQL Server для Oracle CDC осуществляется администратором службы Oracle CDC. Дополнительные сведения о роли администратора службы CDC см. в разделе [User Roles](../../integration-services/change-data-capture/user-roles.md).  
  
### <a name="to-enable-sql-server-for-cdc"></a>Включение SQL Server для CDC  
  
1.  В меню **Пуск** выберите пункт **Конфигурация служб CDC для Oracle**.  
  
2.  На левой панели выберите **Локальные службы CDC** , затем на панели **Действия** щелкните пункт **Подготовка SQL Server**.  
  
     Можно также щелкнуть правой кнопкой **Локальные службы CDC** и выбрать **Подготовить SQL Server**.  
  
3.  Введите необходимую информацию в диалоговом окне «Подготовка экземпляра SQL Server для Oracle CDC». Дополнительную информацию о вводе данных в этом диалоговом окне см. в разделе [Prepare SQL Server for CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md).  
  
     Для подготовки экземпляра SQL Server для Oracle CDC имя входа должно иметь разрешение на запись в базу данных MSXDBCDC. Введите учетные данные для имени входа, имеющего разрешение на запись в базу данных MSXDBCDC. Это может быть член роли `sysasmin` .  
  
 **Примечание.** Можно щелкнуть пункт **Просмотреть скрипт** для просмотра версии скрипта установки, предназначенной только для чтения. Системный администратор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при необходимости может скопировать этот скрипт в консоль управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнить его.  
  
## <a name="see-also"></a>См. также:  
 [Подготовка SQL Server для CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
