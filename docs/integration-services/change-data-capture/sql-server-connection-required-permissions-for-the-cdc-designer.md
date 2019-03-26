---
title: Разрешения, необходимые конструктору CDC для соединения с SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80334de2-17c1-43c9-951e-21a9f864e9cb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b9a95743de7e75620cc1f3b0d07b2d9b42a878f3
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290059"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-designer"></a>Разрешения, необходимые конструктору CDC для соединения с SQL Server
  Консоли конструктора CDC для работы требуются сведения о подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В этом разделе описано, какие данные можно задать в диалоговом окне **Соединение с SQL Server** для настройки соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Диалоговое окно **Соединение с SQL Server** , например, в том случае, когда сведения о соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отсутствуют либо когда у соединения отсутствуют необходимые разрешения.  
  
 В следующей таблице приведено описание различных задач, в рамках которых требуется подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также необходимых разрешений для имени пользователя/пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Задача|Минимальные разрешения|  
|----------|-------------------------|  
|Просмотр списка служб и экземпляров CDC, где используется связанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|`db_datareader` в MSXDBCDC|  
|Запуск и остановка экземпляров CDC|`db_datareader` и `db_datawriter` в MSXDBCDC|  
|Просмотр состояния экземпляра CDC.|`db_owner` в базе данных экземпляра CDC|  
|Создание новой базы данных экземпляра CDC Oracle.|`dbcreator` Предопределенная роль сервера|  
|Создание нового экземпляра CDC Oracle.|`db_datareader` в MSXDBCDC<br /><br /> `db_owner` в базе данных CDC, которая была создана.|  
|Получение скриптов развертывания.|`db_datareader` и `db_datawriter` в MSXDBCDC<br /><br /> `db_owner` в связанной базе данных CDC|  
|Изменение конфигурации, а также добавление и удаление экземпляров отслеживания.|`db_datareader` и `db_datawriter` в MSXDBCDC<br /><br /> `db_owner` в связанной базе данных CDC|  
  
## <a name="see-also"></a>См. также:  
 [Доступ к консоли конструктора CDC](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [Соединение с SQL Server для создания экземпляров](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  
