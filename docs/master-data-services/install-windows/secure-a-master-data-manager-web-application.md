---
title: Обеспечение безопасности веб-приложения диспетчера основных данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 71be238c026dd60db13c10e5d391b8dabdd237dc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="secure-a-master-data-manager-web-application"></a>Обеспечение безопасности веб-приложения диспетчера основных данных

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] можно обезопасить с помощью протокола HTTPS.  
  
> [!NOTE]  
>  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] может использовать протокол HTTP или HTTPS, но не оба.  
  
## <a name="prerequisites"></a>предварительные требования  
 Выполнение процедуры  
  
-   На веб-сервере, где установлен экземпляр служб [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , нужно обладать правами администратора.  
  
-   Службы MDS должны быть установлены на веб-сервере, а веб-приложение должно существовать. Дополнительные сведения см. в статьях [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md) и [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>Обеспечение безопасности веб-приложения диспетчера основных данных с помощью протокола HTTPS  
  
1.  После подтверждения того, что веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] имеет верные настройки протокола HTTP, создайте сертификат на сервере служб IIS. Дополнительные сведения см. в разделе [Настройка сертификатов сервера IIS 7](http://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  На панели **Соединения** на вкладке **Сайты**щелкните сайт, на котором размещено веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
3.  На панели **Действия** щелкните **Привязки**.  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  Выберите **https**из списка.  
  
6.  Выберите SSL-сертификат.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Необязательный параметр. Чтобы удалить из списка протокол HTTP, разрешив доступ к сайту только по протоколу HTTPS, щелкните строку **http**. Нажмите кнопку **Удалить** и в диалоговом окне подтверждения выберите **Да**.  
  
    > [!IMPORTANT]  
    >  Необходимо изменить настройки basicHttp и wsHttpBinding после удаления HTTP.  
  
9. Чтобы закрыть диалоговое окно **Привязки сайтов** , нажмите кнопку **Закрыть**.  
  
10. Теперь откройте файл web.config, который находится в папке *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
11. Найдите строку `<security mode="Message">` и измените ее на строку `<security mode="Transport">`.  
  
12. Сохраните файл и закройте его. Если возникает ошибка, это происходит из-за включенного контроля учетных записей. Дополнительные сведения см. в разделе [Отключение контроля учетных записей](http://technet.microsoft.com/library/cc709691\(WS.10\).aspx). Теперь пользователи могут использовать для доступа к сайту протокол HTTPS.  
  
## <a name="see-also"></a>См. также:  
 [Создание веб-приложения диспетчера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
