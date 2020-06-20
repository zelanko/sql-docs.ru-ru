---
title: Обеспечение безопасности веб-приложения диспетчера основных данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2653ec7ef399083f750d80d9ba7a27e361ecc327
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961644"
---
# <a name="secure-a-master-data-manager-web-application"></a>Обеспечение безопасности веб-приложения диспетчера основных данных
  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] можно обезопасить с помощью протокола HTTPS.  
  
> [!NOTE]  
>  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] может использовать протокол HTTP или HTTPS, но не оба.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Выполнение процедуры  
  
-   На веб-сервере, где установлен экземпляр служб [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , нужно обладать правами администратора.  
  
-   Службы MDS должны быть установлены на веб-сервере, а веб-приложение должно существовать. Дополнительные сведения см. в статьях [Установка служб Master Data Services](install-master-data-services.md) и [Создание веб-приложения мастера основных данных (службы Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>Обеспечение безопасности веб-приложения диспетчера основных данных с помощью протокола HTTPS  
  
1.  После подтверждения того, что веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] имеет верные настройки протокола HTTP, создайте сертификат на сервере служб IIS. Дополнительные сведения см. в разделе [Настройка сертификатов сервера IIS 7](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  На панели **Соединения** на вкладке **Сайты**щелкните сайт, на котором размещено веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
3.  В области **Действия** щелкните элемент **Привязки**.  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  Выберите **https**из списка.  
  
6.  Выберите SSL-сертификат.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Необязательный параметр. Чтобы удалить из списка протокол HTTP, разрешив доступ к сайту только по протоколу HTTPS, щелкните строку **http**. Нажмите кнопку **Удалить** и в диалоговом окне подтверждения выберите **Да**.  
  
    > [!IMPORTANT]  
    >  Необходимо изменить настройки basicHttp и wsHttpBinding после удаления HTTP.  
  
9. Чтобы закрыть диалоговое окно **Привязки сайтов** , нажмите кнопку **Закрыть**.  
  
10. Теперь откройте web.config файл с *диска*: \PROGRAM Files\Microsoft SQL Server\120\Master Data Services\WebApplication.  
  
11. Найдите строку `<security mode="Message">` и измените ее на строку `<security mode="Transport">`.  
  
12. Сохраните файл и закройте его. Если возникает ошибка, это происходит из-за включенного контроля учетных записей. Дополнительные сведения см. в разделе [Отключение контроля учетных записей](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx). Теперь пользователи могут использовать для доступа к сайту протокол HTTPS.  
  
## <a name="see-also"></a>См. также:  
 [Создание веб-приложения мастера основных данных (службы Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md)  
  
  
