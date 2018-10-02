---
title: Проверка разрешений пользователя (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8ddcd6d754ce1b760d91462847b796e4ec8de933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47594612"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Проверка разрешений пользователя (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать тестовую учетную запись и войти в веб-приложение для проверки разрешений. При попытке пользователя получить доступ к URL-адресу [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выполняется проверка учетных данных пользователя. В Internet Explorer в зависимости от параметров безопасности проверка подлинности будет выполнена автоматически либо пользователю придется ввести имя и пароль. Чтобы изменить эти настройки, выполните следующие действия.  
  
### <a name="to-test-a-users-security"></a>Проверка безопасности пользователя  
  
1.  В Internet Explorer версии 7 и выше выберите в меню **Сервис**пункт **Свойства обозревателя**и перейдите на вкладку **Безопасность** .  
  
2.  Нажмите **Местная интрасеть** , затем нажмите кнопку **Другой** .  
  
3.  В разделе **Проверка подлинности пользователя** выберите **Запрос имени пользователя и пароля**.  
  
4.  При следующем открытии окна браузера будет предложено указать имя пользователя и пароль.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность (службы Master Data Services)](../master-data-services/security-master-data-services.md)  
  
  
