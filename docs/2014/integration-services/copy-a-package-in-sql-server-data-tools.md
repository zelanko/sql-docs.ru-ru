---
title: Копирование пакета с помощью SQL Server Data Tools | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 673b69ea632108b889cc2f99b63c9c602ef05237
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62829540"
---
# <a name="copy-a-package-in-sql-server-data-tools"></a>Копирование пакета с помощью SQL Server Data Tools
  В этом разделе описывается, как создать новый пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] копированием существующего пакета и как обновить свойства `Name` и `GUID` нового пакета.  
  
### <a name="to-copy-a-package"></a>Копирование пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий пакет, который нужно скопировать.  
  
2.  Дважды щелкните пакет в обозревателе решений.  
  
3.  Убедитесь, что копируемый пакет выбран в обозревателе решений либо в конструкторе служб SSIS выбрана вкладка, содержащая пакет  
  
4.  В меню **Файл** выберите команду **Сохранить \<имя пакета> как**.  
  
    > [!NOTE]  
    >  Чтобы команда **Сохранить как** появилась в меню **Файл** , пакет нужно открыть в конструкторе служб SSIS.  
  
5.  При необходимости перейдите в другую папку.  
  
6.  Обновите имя файла пакета. Убедитесь, что файл сохраняется с расширением DTSX.  
  
7.  Выберите команду **Сохранить**.  
  
8.  Выберите, обновлять ли имя объекта пакета, чтобы оно соответствовало имени файла. Если нажать кнопку **Да**, `Name` свойство пакета будет обновлено. Новый пакет будет добавлен к проекту служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и открыт в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
9. При необходимости перейдите на вкладку **Поток управления** и выберите **Свойства**.  
  
10. В окне "Свойства" щелкните значение свойства идентификатора (ID), а затем выберите **\<Сформировать новый идентификатор>** в раскрывающемся списке.  
  
11. В меню **Файл** выберите команду **Сохранить выбранные элементы** , чтобы сохранить новый пакет.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение одной копии пакета](../../2014/integration-services/save-a-copy-of-a-package.md)   
 [Создание пакетов в SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)   
 [Пакеты служб Integration Services (SSIS)](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
