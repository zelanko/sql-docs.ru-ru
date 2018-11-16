---
title: Обновление схемы базы данных DQS после установки обновления SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a3743dbd355f2f6a45e3a73559a1bef93f8f2dd9
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699742"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a>Обновление схемы базы данных DQS после установки обновления SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  После установки обновления SQL Server (обновления, исправления или накопительного обновления) на ранее настроенном экземпляре DQS можно обновить схему баз данных DQS, запустив файл DQSInstaller.exe с параметром командной строки **upgrade**. В противном случае может появиться сообщение об ошибке при попытке соединения с сервером DQS через клиент Data Quality:  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 Обновление схемы баз данных DQS не влияет на существующие данные в базах данных DQS (базах знаний, проектах качества данных и экспортированные результаты в базе данных DQS_STAGING_DATA). Однако необходимо создать резервную копию баз данных DQS, прежде чем обновлять схему баз данных DQS, чтобы предотвратить любую случайную потерю данных при обновлении схемы. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
> [!NOTE]  
>  Большинство обновлений SQL Server требует обновления схемы баз данных DQS. Дополнительные сведения об обновлениях SQL Server, которые требуют обновления до схемы баз данных DQS, см. в диаграмме на шаге 1.А в статье [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Обновления службы DQS: установка накопительных обновлений или исправлений для служб Data Quality Services).  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо выполнить вход от имени члена группы администраторов на компьютере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Учетная запись пользователя Windows должна входить в предопределенную роль сервера sysadmin на экземпляре SQL Server, где установлен сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
### <a name="to-upgrade-dqs-databases-schema"></a>Обновление схемы базы данных DQS  
  
1.  (Рекомендуется) Создать резервную копию баз данных DQS, прежде чем продолжить обновление схемы. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
2.  Откройте командную строку.  
  
3.  В командной строке перейдите в папку, где находится файл DQSInstaller.exe. Если был установлен экземпляр SQL Server по умолчанию, файл DQSInstaller.exe будет находиться в папке C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  Установщик предложит создать резервную копию базы данных DQS, прежде чем продолжить. Если резервное копирование базы данных DQS уже выполнено, введите **Y** или **Yes** и нажмите клавишу ВВОД, чтобы продолжить обновление.  
  
6.  После успешного обновления схемы баз данных DQS отображается сообщение о завершении.  
  
## <a name="next-steps"></a>Next Steps  
 Войдите на обновленный сервер из клиентского приложения Data Quality.  
  
 Дополнительные сведения об обновлении схемы баз данных DQS после установки обновлений SQL Server и о шагах по устранению связанных с обновлением неполадок см. в статье [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Обновления службы DQS: установка накопительных обновлений или исправлений для служб Data Quality Services).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Обновление сборок SQLCLR после загрузки обновлений .NET Framework](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
