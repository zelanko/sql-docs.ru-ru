---
description: Проверка диалогового окна
title: Диалоговое окно "Проверка" | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.isprojectvalidate.f1
- sql13.ssis.ssms.ispackagevalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a65f5d8114907472eb03aa06e428927aa1408b7b
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88484937"
---
# <a name="validate-dialog-box"></a>Проверка диалогового окна

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Воспользуйтесь диалоговым окном **Проверка** для поиска типичных проблем в проекте или пакете служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 При обнаружении проблемы в верхней части диалогового окна отображается сообщение. В противном случае в верхней части диалогового окна отображается сообщение «Готово».  
  
 **Выбор действия**  
  
-   [Открытие диалогового окна «Проверка»](#open_dialog)  
  
-   [Задание параметров на странице «Общие»](#general)  
  
##  <a name="open-the-validate-dialog-box"></a><a name="open_dialog"></a> Открытие диалогового окна «Проверка»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Устанавливается соединение с экземпляром [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], в котором размещена база данных SSISDB.  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Разверните узел **SSISDB** .  
  
4.  Разверните папку, содержащую проект или пакет, который требуется проверить.  
  
5.  Щелкните правой кнопкой мыши пакет или проект и выберите **Проверить**.  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> Задание параметров на странице «Общие»  
 **Среда**  
 Выберите среду, которая будет использована для проверки проекта или пакета.  
  
 **32-разрядная среда выполнения**  
 Для выполнения пакета выберите 32-разрядную среду выполнения.  
  
 На вкладке **Параметры** перечислены значения параметров, которые используются для проверки проекта или пакета. Ниже приведены параметры на вкладке «Параметры».  
  
 **Контейнер**  
 Выводит список объектов, содержащих параметр.  
  
 **Параметр**  
 Выводит список названий параметров  
  
 **Значение**  
 Выводит список значений параметра.  
  
 На вкладке **Диспетчеры соединений** перечислены значения свойств диспетчеров соединений, которые используются для проверки проекта или пакета.  
  
 Ниже приведены параметры на вкладке **Диспетчеры соединений** .  
  
 **Контейнер**  
 Выводит список объектов, содержащих диспетчер соединений.  
  
 **имя**;  
 Выводит список имен диспетчеров соединений.  
  
 **Имя свойства**  
 Выводит список названий свойств диспетчера соединений.  
  
 **Значение**  
 Выводит список значений, присвоенных свойствам диспетчера соединений.  
  
  
