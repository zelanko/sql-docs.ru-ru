---
title: Запуск пакета в SQL Server Data Tools | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 23fd9f18468fa084ed526ab93f993a545749b2e1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190470"
---
# <a name="run-a-package-in-sql-server-data-tools"></a>Запуск пакета с помощью SQL Server Data Tools
  Обычно пакеты исполняются в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] во время разработки, отладки и тестирования пакетов. Когда пакет запускается из конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , его запуск происходит немедленно.  
  
 Во время выполнения пакета конструктор служб [!INCLUDE[ssIS](../includes/ssis-md.md)] отображает ход выполнения пакета на вкладке **Выполнение** . Можно видеть время начала и завершения выполнения пакета, его задачи и контейнеры — наряду с данными о задачах или контейнерах пакета, завершившегося ошибкой. По завершении выполнения пакета на вкладке **Результаты выполнения** сохраняются сведения о ходе выполнения. Дополнительные сведения см. в подразделе «Отчет о состоянии» раздела [Debugging Control Flow](control-flow/control-flow.md).  
  
 **Развертывание времени проектирования**. Когда запуск пакета произведен в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], происходит построение пакета и затем его развертывание в папку. Перед запуском пакета можно указать папку, в которой будет производиться развертывание пакета. Если папка не указана, то по умолчанию используется папка **bin** . Этот тип развертывания называется развертыванием времени разработки.  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>Запуск пакета с помощью SQL Server Data Tools  
  
1.  Если решение содержит несколько проектов, щелкните в обозревателе решений правой кнопкой мыши папку проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], содержащую пакет, и задайте стартовый проект, выбрав пункт **Установить в качестве автоматически запускаемого объекта**.  
  
2.  Если проект содержит несколько пакетов, щелкните в обозревателе решений правой кнопкой мыши пакет и задайте стартовый пакет, выбрав пункт **Установить в качестве автоматически запускаемого объекта** .  
  
3.  Чтобы запустить пакет, выполните одну из следующих процедур.  
  
    -   Откройте пакет, который необходимо запустить, затем выберите пункт **Начать отладку** в меню или нажмите клавишу F5. После исполнения пакета нажмите клавиши Shift+F5 для возврата в режим конструктора.  
  
    -   В обозревателе решений щелкните правой кнопкой мыши пакет, после чего выберите пункт **Выполнить пакет**.  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>Задание каталога для развертывания времени разработки  
  
1.  В обозревателе решений щелкните правой кнопкой мыши папку проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], содержащую запускаемый пакет, затем выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Страницы свойств \<имя проекта>** выберите элемент **Сборка**.  
  
3.  Обновите значения свойства OutputPath для указания папки, которую необходимо использовать для развертывания времени разработки, и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Запуск проектов и пакетов](packages/run-integration-services-ssis-packages.md)   
 [Пакеты служб Integration Services (SSIS)](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  