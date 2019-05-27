---
title: 'Подключение к данным использует проверку подлинности Windows, а учетные данные нельзя делегировать. Следующие соединения не удалось обновить: Данные PowerPivot | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0b11e1510213aefa98c6bf2c0c779cebaeed85e5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66071031"
---
# <a name="the-data-connection-uses-windows-authentication-and-user-credentials-could-not-be-delegated-the-following-connections-failed-to-refresh-powerpivot-data"></a>Подключение к данным использует проверку подлинности Windows, а учетные данные нельзя делегировать. Следующие соединения не удалось обновить: данные PowerPivot
  Служба Excel Services возвращает эту ошибку для книг Excel, содержащих данные PowerPivot, если она не может подключиться к экземпляру сервера PowerPivot в SharePoint.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Применение|PowerPivot для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Сбой соединения при попытке использовать поставщик данных PowerPivot.|  
|Текст сообщения|Подключение к данным использует проверку подлинности Windows, а учетные данные нельзя делегировать. Следующие соединения не удалось обновить: данные PowerPivot|  
  
## <a name="explanation"></a>Объяснение  
 Есть несколько причин возникновения этого сообщения об ошибке. Общим для всех них является то, что служба Excel Services не может получить действительное удостоверение пользователя Windows из токена утверждений в SharePoint. При работе с книгами Excel, которые содержат данные PowerPivot, эта ошибка возникает при наличии любого из следующих условий.  
  
-   Служба Claims to Windows Token Service не работает. Подтвердить причину этой ошибки можно, открыв файл журнала SharePoint. Если в журналах SharePoint есть сообщение «Конечная точка конвейера 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' не обнаружена на локальном компьютере», значит служба Claims to Windows Token Service не работает. Воспользуйтесь центром администрирования, чтобы запустить ее, а затем удостоверьтесь, что она работает в консольном приложении «Службы».  
  
-   Контроллер домена недоступен для проверки удостоверения пользователя. Служба Claims to Windows Token Service не использует кэшированные учетные данные. Она проверяет удостоверение пользователя для каждого соединения. Подтвердить причину этой ошибки можно, открыв файл журнала SharePoint. Если в журналах SharePoint есть сообщение «Не удалось получить WindowsIdentity от IClaimsIdentity», то подлинность удостоверения пользователя не удалось проверить.  
  
-   Компьютеры должны входить в один домен или в домены с двусторонними отношениями доверия.  
  
-   Необходимо использовать учетные записи пользователей домена Windows. Учетные записи должны иметь универсальное имя участника (UPN).  
  
-   Чтобы запрашивать объект, учетная запись службы Excel Services должна иметь разрешения для Active Directory.  
  
## <a name="user-action"></a>Действие пользователя  
 Следуйте приведенным далее инструкциям для проверки состояния службы Claims to Windows Token Service.  
  
 Сведения обо всех прочих сценариях можно получить у своего сетевого администратора.  
  
#### <a name="enable-claims-to-windows-token-service"></a>Включите службу Claims to Windows Token Service  
  
1.  В центре администрирования в области «Системные параметры» щелкните ссылку **Управление службами на сервере**.  
  
2.  Выберите **Claims to Windows Token Service**, а затем нажмите кнопку **Пуск**.  
  
3.  Также убедитесь в том, что служба запущена, в консоли «Службы».  
  
    1.  В окне «Средства администрирования» выберите «Службы».  
  
    2.  Запустите службу Claims to Windows Token Service, если она не работает.  
  
## <a name="see-also"></a>См. также  
 [Указание учетных записей служб PowerPivot](configure-power-pivot-service-accounts.md)  
  
  
