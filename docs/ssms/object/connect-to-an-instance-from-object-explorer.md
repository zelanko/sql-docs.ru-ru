---
description: Подключение к SQL Server или базе данных SQL Azure
title: Подключение к SQL Server или базе данных SQL Azure
ms.custom: seo-lt-2019
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2530029b43a4b01d8b6fce8b321f0c9b66a6a852
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417940"
---
# <a name="connect-to-a-sql-server-or-azure-sql-database"></a>Подключение к SQL Server или базе данных SQL Azure

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Для работы с серверами и базами данных необходимо сначала подключиться к серверу. Вы можете подключаться к нескольким серверам одновременно.

[SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) поддерживает несколько типов подключений. Эта статья содержит сведения о подключении к SQL Server и Базе данных SQL Azure (подключение к отдельной базе данных или эластичному пулу SQL Azure). Сведения о других вариантах подключения см. по [ссылкам](#see-also) в нижней части страницы.
  
## <a name="connecting-to-a-server"></a>Соединение с сервером  

1. В **Обозревателе объектов** щелкните **Подключиться > Ядро СУБД…**.

   ![подключение](../media/connect-to-server/connect-db-engine.png)

1. Заполните форму **Подключение к серверу** и щелкните **Подключиться**.

   ![подключение к серверу](../media/connect-to-server/connect.png)

1. При подключении к серверу SQL Azure вы можете получить запрос на вход в систему для создания правила брандмауэра. Щелкните **Войти…** (в противном случае перейдите к шагу 6 ниже)

   ![брандмауэр](../media/connect-to-server/firewall-rule-sign-in.png)

1. После выполнения входа в систему в форме появится ваш IP-адрес. Если ваш IP-адрес часто меняется, возможно, проще предоставить доступ для диапазона адресов. Выберите вариант, который лучше всего подходит для вашей среды. 

   ![брандмауэр](../media/connect-to-server/new-firewall-rule.png)

1. Чтобы создать правило брандмауэра и подключиться к серверу, нажмите кнопку **ОК**.

1. После подключения сервер появится в **Обозревателе объектов**.

   ![connected](../media/connect-to-server/connected.png)

## <a name="next-steps"></a>Next Steps

[Проектирование, создание и изменение таблиц](../visual-db-tools/design-tables-visual-database-tools.md)

## <a name="see-also"></a>См. также:

[SQL Server Management Studio (SSMS)](../sql-server-management-studio-ssms.md)  
[Скачивание SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)

[Службы Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)  
[Службы интеграции](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)  
[службы Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)  
[Хранилище Azure](../f1-help/connect-to-microsoft-azure-storage.md)  
