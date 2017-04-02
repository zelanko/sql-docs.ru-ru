---
title: "Обеспечение безопасности веб-приложения диспетчера основных данных | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Обеспечение безопасности веб-приложения диспетчера основных данных
  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] можно обезопасить с помощью протокола HTTPS.  
  
> [!NOTE]  
>  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] может использовать протокол HTTP или HTTPS, но не оба.  
  
## Предварительные требования  
 Выполнение процедуры  
  
-   На веб-сервере, где установлен экземпляр служб [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , нужно обладать правами администратора.  
  
-   Службы MDS должны быть установлены на веб-сервере, а веб-приложение должно существовать. Дополнительные сведения см. в статьях [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md) и [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
### Обеспечение безопасности веб-приложения диспетчера основных данных с помощью протокола HTTPS  
  
1.  После подтверждения того, что веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] имеет верные настройки протокола HTTP, создайте сертификат на сервере служб IIS. Дополнительные сведения см. в разделе [Настройка сертификатов сервера IIS 7](http://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  На панели **Соединения** на вкладке **Сайты**щелкните сайт, на котором размещено веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
3.  На панели **Действия** щелкните **Привязки**.  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  Выберите **https**из списка.  
  
6.  Выберите SSL-сертификат.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Необязательно. Чтобы удалить из списка протокол HTTP, разрешив доступ к сайту только по протоколу HTTPS, щелкните строку **http**. Нажмите кнопку **Удалить** и в диалоговом окне подтверждения выберите **Да**.  
  
    > [!IMPORTANT]  
    >  Необходимо изменить настройки basicHttp и wsHttpBinding после удаления HTTP.  
  
9. Чтобы закрыть диалоговое окно **Привязки сайтов** , нажмите кнопку **Закрыть**.  
  
10. Теперь откройте файл web.config, который находится в папке *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
11. Найдите строку `<security mode="Message">` и измените ее на строку `<security mode="Transport">`.  
  
12. Сохраните файл и закройте его. Если возникает ошибка, это происходит из-за включенного контроля учетных записей. Дополнительные сведения см. в разделе [Отключение контроля учетных записей](http://technet.microsoft.com/library/cc709691\(WS.10\).aspx). Теперь пользователи могут использовать для доступа к сайту протокол HTTPS.  
  
## См. также:  
 [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  