---
title: Диалоговое окно "Свойства пакета" | Документация Майкрософт
ms.custom: ''
ms.date: 08/26/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.ispackageprop.general.f1
- sql13.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8e392e406ce9c17cc24f57a22cef03de2c363a21
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58289057"
---
# <a name="package-properties-dialog-box"></a>диалоговое окно «Свойства пакета»
  Используйте диалоговое окно **Свойства пакета** для просмотра свойств пакетов, хранящихся на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Дополнительные сведения см. в разделе [Службы Integration Services (сервер служб SSIS)](../integration-services-ssis-packages.md).  
  
 **Выбор действия**  
  
-   [Открытие диалогового окна «Свойства пакета»](#open_dialog)  
  
-   [Настройка параметров](#options)  
  
##  <a name="open_dialog"></a> Открытие диалогового окна «Свойства пакета»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Устанавливается соединение с экземпляром [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], в котором размещена база данных SSISDB.  
  
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
  
  
