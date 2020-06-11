---
title: Создание веб-приложения диспетчера основных данных
description: Диспетчер основных данных веб-приложение предоставляет пользователям интерфейс для работы с основными данными, а администраторам — для настройки и администрирования MDS.
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 241d46d7-8008-47f6-bebd-0dfff1cc856a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 84da8c7a87901ddcb964773bea2f330ea86a742e
ms.sourcegitcommit: 903856818acc657e5c42faa16d1c770aeb4e1d1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2020
ms.locfileid: "83731695"
---
# <a name="create-a-master-data-manager-web-application-master-data-services"></a>Создание веб-приложения диспетчера основных данных (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] предоставляет интерфейс пользователям для работы с основными данными, а администраторам — для настройки и администрирования MDS.  
  
 Веб-приложение всегда должно располагаться на веб-сайте. Для создания веб-приложения можно использовать один из следующих способов.  
  
-   Использовать веб-сайт по умолчанию, а затем создать веб-приложение.  
  
-   Использовать существующий веб-сайт, а затем создать веб-приложение.  
  
-   Создать новый веб-сайт с автоматическим созданием нового веб-приложения.  
  
 После того как вы создали веб-приложение, необходимо связать его с базой данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Дополнительные сведения о требованиях, предъявляемых к компьютеру, на котором размещается веб-приложение, см. в разделе [Требования веб-приложений (Master Data Services)](../../master-data-services/install-windows/web-application-requirements-master-data-services.md).  
  
## <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a>Создание веб-приложения диспетчера основных данных на новом веб-сайте  
 При создании нового веб-сайта корневое веб-приложение является веб-приложением [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Это веб-приложение будет также добавляется в новый пул приложений.  
  
> [!NOTE]  
>  При выполнении этой процедуры нельзя указать виртуальный путь и псевдоним для веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . Если необходимо указать виртуальный путь и псевдоним для [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], веб-приложение следует создать на существующем веб-сайте, причем он не должен быть настроен в качестве веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
 Следует также учитывать, что [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] поддерживает создание сайтов только с HTTP-привязками. Для добавления привязки HTTPS создайте новый сайт и приложение в [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , а затем см. дополнительные сведения в разделе [Обеспечение безопасности веб-приложения диспетчера основных данных](../../master-data-services/install-windows/secure-a-master-data-manager-web-application.md) .  
  
#### <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a>Создание веб-приложения диспетчера основных данных на новом веб-сайте  
  
1.  Откройте [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
3.  На странице **Веб-конфигурация** в списке «Веб-сайт» выберите **Создать новый веб-сайт**.  
  
4.  В диалоговом окне **Создание веб-сайта** укажите данные для нового веб-сайта. Дополнительные сведения о параметрах пользовательского интерфейса в этом диалоговом окне см. в разделе [Диалоговое окно "Создание веб-сайта" (диспетчер конфигурации Master Data Services)](../../master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a>Создание веб-приложения диспетчера основных данных на существующем веб-сайте  
 При создании веб-приложения на существующем веб-сайте для него можно выбрать виртуальный путь и псевдоним. Это веб-приложение будет добавлено в новый пул приложений.  
  
#### <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a>Создание веб-приложения диспетчера основных данных на существующем веб-сайте  
  
1.  Откройте [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
3.  На странице **Веб-конфигурация** в списке **Веб-сайт** выберите веб-сайт, на котором нужно создать веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
4.  Нажмите кнопку **Создать приложение**.  
  
5.  В диалоговом окне **Создание веб-приложения** укажите данные для нового веб-приложения. Дополнительные сведения о параметрах пользовательского интерфейса в этом диалоговом окне см. в разделе [Диалоговое окно "Создание веб-приложения" (диспетчер конфигурации Master Data Services)](../../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
6.  Нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Свяжите веб-приложение с базой данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Связывание базы данных служб Master Data Services и веб-приложения](../../master-data-services/install-windows/associate-a-master-data-services-database-and-web-application.md).  
  
-   При необходимости можно настроить веб-сайт, на котором размещено [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] веб-приложение, использовать привязку HTTPS, если требуется шифровать содержимое с помощью протокола TLS, ранее известного как SSL (SSL). Для настройки сертификата сервера для веб-сервера и настройки привязки HTTPS и параметров TLS для сайта необходимо использовать средство службы IIS (IIS), например диспетчер IIS. Дополнительные сведения см. в статье [Secure a Master Data Manager Web Application](../../master-data-services/install-windows/secure-a-master-data-manager-web-application.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
