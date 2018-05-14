---
title: Свойства сервера (страница "Общие") — среда SQL Server Management Studio | Документы Майкрософт
ms.custom: ''
ms.date: 08/25/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.setsapassword.f1
- sql13.swb.serverproperties.activedirectory.f1
- sql13.swb.serverproperties.prodinfo.f1
ms.assetid: 10ac57f1-b4bd-4528-bb66-3e47ccf663e7
caps.latest.revision: 30
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 34c019dfd0d4fd443c61eb0993359dd63883ffa5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="server-properties---general-page"></a>Свойства сервера (страница "Общие")
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Эта страница выводит доступные только для чтения данные об установленной конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="property-grid"></a>Сетка свойств  
 Показывает свойства выбранного сервера — имя сервера, установленную ОС и число процессоров.  
  
 **Название**  
 Отображает имя экземпляра сервера.  
  
 **Продукт**  
 Выводит выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенный в данный момент.  
  
 **Операционная система**  
 Отображает версию работающей в настоящий момент ОС [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Платформа**  
 Описывает ОС и оборудование, на которых запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Версия**  
 Выводит номер версии запущенного в настоящий момент выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Язык**  
 Выводит язык, поддерживаемый запущенным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Память**  
 Выводит объем ОЗУ, установленного на данном сервере.  
  
 **Процессоры**  
 Выводит число установленных ЦП.  
  
 **Корневой каталог**  
 Выводит путь к данному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , обычно "C:\Program Files\Microsoft SQL Server\\".  
  
 **Параметры сортировки сервера**  
 Выводит параметры сортировки, поддерживаемые сервером. Параметры сортировки задают кодовую страницу и порядок сортировки для работы с данными в Юникоде и других форматах.  
  
 **Кластеризован**  
 Содержит значение **True** , если экземпляр сервера настроен для работы в отказоустойчивом кластере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо значение **False** , если экземпляр сервера не кластеризован.  
  
 **Режим HADR включен**  
 Содержит значение **True** , если служба [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] включена, или **False** , если служба [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] отключена. Дополнительные сведения о включении и отключении [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] см. в статье [Включение и отключение групп доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
## <a name="description-field"></a>Поле описания  
 Содержит дополнительные сведения о свойствах сервера.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
