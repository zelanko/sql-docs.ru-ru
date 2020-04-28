---
title: Предоставление доступа к данным для операций со службами DQS
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 2eae5415e6f6bb93501dfc7989fe180e581ae387
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75254792"
---
# <a name="access-data-for-the-dqs-operations"></a>Предоставление доступа к данным для операций со службами DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Чтобы использовать исходные данные для операций служб [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) и экспортировать обработанные данные, выполните одно из следующих действий.  
  
-   Скопируйте исходные данные в таблицу или представление в базе данных DQS_STAGING_DATA, а затем передайте данную таблицу или представление на обработку операции DQS. Можно также выполнить экспорт обработанных данных в новую таблицу в базе данных DQS_STAGING_DATA. Для этого учетной записи пользователя Windows должен быть предоставлен доступ на чтение и запись к базе данных DQS_STAGING_DATA.  
  
-   Собственная база данных может использоваться как в качестве исходных данных для операций служб DQS, так и для экспорта обработанных данных. Для этого убедитесь, что она размещена на том же экземпляре SQL Server, что и базы данных сервера служб Data Quality. В противном случае база данных не будет доступна в клиенте служб Data Quality для операций DQS. Также для учетной записи пользователя Windows должен быть предоставлен доступ к базе данных DQS_STAGING_DATA для экспорта соответствующих результатов, так как они экспортируются в два этапа: сначала экспортируются во временные таблицы в базе данных DQS_STAGING_DATA, а затем перемещаются в таблицу целевой базы данных.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо, чтобы установка сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , запускаемая с помощью файла DQSInstaller.exe, была завершена. Дополнительные сведения см. в разделе [Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   Учетная запись пользователя Windows должна входить в соответствующую предопределенную роль сервера (например, securityadmin, serveradmin или sysadmin) на экземпляре компонента Database Engine для предоставления и изменения доступа имени входа SQL Server к базам данных.  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqs_staging_data-database"></a>Предоставление доступа на чтение и запись пользователям базы данных DQS_STAGING_DATA  
  
1.  Запустите среду Microsoft SQL Server Management Studio.  
  
2.  В среде Microsoft SQL Server Management Studio разверните узел экземпляра SQL Server, а затем узлы **Безопасность**и **Имена входа**.  
  
3.  Правой кнопкой мыши щелкните имя входа SQL Server и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства имени входа** щелкните страницу **Сопоставление пользователей** в левой части.  
  
5.  На правой панели установите флажок в столбце **Сопоставление** для базы данных **DQS_STAGING_DATA** , а затем выберите следующие роли в панели **Членство в роли базы данных для DQS_STAGING_DATA** :  
  
    -   **db_datareader**: чтение данных из таблиц и представлений.  
  
    -   **db_datawriter**: добавление, удаление и изменение данных в таблицах.  
  
    -   **db_ddladmin**: создание, изменение или удаление таблиц и представлений.  
  
6.  В диалоговом окне **Свойства имени входа** нажмите кнопку **ОК** , чтобы применить изменения.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Проверьте работоспособность операций служб DQS, использующих эту базу данных в качестве источника данных, а затем экспортирующих в нее обработанные данные.  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)  
  
  
