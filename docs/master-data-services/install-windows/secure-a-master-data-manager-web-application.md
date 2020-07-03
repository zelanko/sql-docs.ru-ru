---
title: Обеспечение безопасности веб-приложения диспетчера основных данных
description: В SQL Server можно защитить диспетчер основных данных веб-приложение с помощью протокола HTTPS. Необходимо быть администратором, и службы MDS должны быть установлены на веб-сервере.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 542828e26b82d0df0174886f706117feb8ad2322
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883834"
---
# <a name="secure-a-master-data-manager-web-application"></a>Обеспечение безопасности веб-приложения диспетчера основных данных

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] можно обезопасить с помощью протокола HTTPS.  
  
> [!NOTE]  
>  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] может использовать протокол HTTP или HTTPS, но не оба.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Выполнение процедуры  
  
-   На веб-сервере, где установлен экземпляр служб [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , нужно обладать правами администратора.  
  
-   Службы MDS должны быть установлены на веб-сервере, а веб-приложение должно существовать. Дополнительные сведения см. в статьях [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md) и [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>Обеспечение безопасности веб-приложения диспетчера основных данных с помощью протокола HTTPS  
  
1.  После подтверждения того, что веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] имеет верные настройки протокола HTTP, создайте сертификат на сервере служб IIS. Дополнительные сведения см. в разделе [Настройка сертификатов сервера IIS 7](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  На панели **Соединения** на вкладке **Сайты**щелкните сайт, на котором размещено веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
3.  В области **Действия** щелкните элемент **Привязки**.  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  Выберите **https**из списка.  
  
6.  Выберите сертификат TLS/SSL.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Необязательный элемент. Чтобы удалить из списка протокол HTTP, разрешив доступ к сайту только по протоколу HTTPS, щелкните строку **http**. Нажмите кнопку **Удалить** и в диалоговом окне подтверждения выберите **Да**.  
  
    > [!IMPORTANT]  
    >  Необходимо изменить настройки basicHttp и wsHttpBinding после удаления HTTP.  
  
9. Чтобы закрыть диалоговое окно **Привязки сайтов** , нажмите кнопку **Закрыть**.  
  
10. Теперь откройте файл web.config, который находится в папке *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
11. Найдите строку `<security mode="Message">` и измените ее на строку `<security mode="Transport">`.  

12. Измените `<serviceMetadata httpGetEnable="true" httpsGetEnabled="false">` на `<serviceMetadata httpGetEnable="false" httpsGetEnabled="true">`, чтобы предотвратить проблемы, которые могут появиться в клиенте Silverlight.

13. Сохраните файл и закройте его. Если возникает ошибка, это происходит из-за включенного контроля учетных записей. Теперь пользователи могут использовать для доступа к сайту протокол HTTPS.  

  
## <a name="see-also"></a>См. также  
 [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
