---
title: "Диалоговое окно \"Свойства пакета\" | Документация Майкрософт"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.ssms.ispackageprop.general.f1
- sql13.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a87d391fd878028aeabdebab8fb62054560cbfe
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="package-properties-dialog-box"></a>диалоговое окно «Свойства пакета»
  Используйте диалоговое окно **Свойства пакета** для просмотра свойств пакетов, хранящихся на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Дополнительные сведения см. в разделе [Службы Integration Services (сервер служб SSIS)](../integration-services-ssis-packages.md).  
  
 **Выбор действия**  
  
-   [Открытие диалогового окна «Свойства пакета»](#open_dialog)  
  
-   [Настройка параметров](#options)  
  
##  <a name="open_dialog"></a> Открытие диалогового окна «Свойства пакета»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Устанавливается соединение с экземпляром компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , в котором размещена база данных SSISDB.  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Разверните узел **SSISDB** .  
  
4.  Разверните папку, содержащую пакет, свойства которого требуется просмотреть.  
  
5.  Щелкните правой кнопкой мыши пакет и выберите **Свойства**.  
  
##  <a name="options"></a> Настройка параметров  
 На странице **Общие** можно просмотреть свойства выбранного пакета.  
  
 Все свойства на странице **Общие** доступны только для чтения.  
  
 **Название**  
 Отображает имя пакета.  
  
 **Идентификатор**  
 Выводит идентификатор пакета.  
  
 **Точка входа**  
 Значение **True** указывает, что пакет запущен непосредственно. Значение **False** указывает, что пакет запущен из другого пакета с помощью задачи «Выполнение пакета». Значение по умолчанию ― **True**.  
  
 Это свойство задается в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] как для родительского пакета, так и для дочерних пакетов. Для этого щелкните пакет правой кнопкой мыши в обозревателе решений, а затем выберите **Входной пакет**.  
  
 **Описание**  
 Показывает необязательное описание пакета.  
  
  
