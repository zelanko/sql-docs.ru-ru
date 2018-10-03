---
title: Проверка разрешений пользователя (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 6c506123c772e1063713fc81f32fdbbaa0d5c8f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051084"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Проверка разрешений пользователя (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать тестовую учетную запись и войти в веб-приложение для проверки разрешений. При попытке пользователя получить доступ к URL-адресу [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выполняется проверка учетных данных пользователя. В Internet Explorer в зависимости от параметров безопасности проверка подлинности будет выполнена автоматически либо пользователю придется ввести имя и пароль. Чтобы изменить эти настройки, выполните следующие действия.  
  
### <a name="to-test-a-users-security"></a>Проверка безопасности пользователя  
  
1.  В Internet Explorer версии 7 и выше выберите в меню **Сервис**пункт **Свойства обозревателя**и перейдите на вкладку **Безопасность** .  
  
2.  Нажмите **Местная интрасеть** , затем нажмите кнопку **Другой** .  
  
3.  В разделе **Проверка подлинности пользователя** выберите **Запрос имени пользователя и пароля**.  
  
4.  При следующем открытии окна браузера будет предложено указать имя пользователя и пароль.  
  
## <a name="see-also"></a>См. также  
 [Безопасность (службы Master Data Services)](security-master-data-services.md)  
  
  
