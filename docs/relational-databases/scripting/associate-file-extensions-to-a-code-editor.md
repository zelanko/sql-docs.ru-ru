---
title: Связывание расширения файла с редактором кода | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cc15f3b703a8c60be40ecb42e595db8540c1cfbe
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="associate-file-extensions-to-a-code-editor"></a>Связывание расширения файла с редактором кода
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Связь расширений файлов с конкретным редактором кода позволяет открывать файл соответствующим редактором кода среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] двойным щелчком файла в проводнике Windows. Расширения, обычно используемые средой [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], такие как SQL и MDX, задаются во время установки. Новые расширения файлов должны быть связаны со средой [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] в файловой системе. Эту возможность можно использовать для открытия файлов, созданных в других редакторах, или для открытия переименованных файлов, таких как резервные копии SQL-файлов, переименованных в файлы с расширением BAK.  
  
 Этот процесс включает два шага. Вначале нужно связать расширение со средой [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем — с конкретным редактором кода.  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a>Связывание нового расширения файла со средой SQL Server Management Studio  
  
1.  В меню **Пуск** последовательно укажите **Все программы**, **Стандартные**, **Проводник**.  
  
2.  В проводнике Windows в меню **Сервис** выберите **Свойства папки**.  
  
3.  В диалоговом окне **Свойства папки** на вкладке **Типы файлов** нажмите кнопку **Создать**.  
  
4.  В диалоговом окне **Создание нового расширения** в поле **Расширение** введите новое расширение файла, которое нужно задать, и нажмите кнопку **ОК**. Не ставьте перед расширением точку.  
  
5.  В списке **Зарегистрированные типы файлов** выберите новое расширение и нажмите **Изменить**.  
  
6.  В диалоговом окне **Открыть с помощью** выберите пункт **SSMS — среда SQL Server Management Studio**и нажмите кнопку **ОК**.  
  
7.  Нажмите **Закрыть** , чтобы закрыть диалоговое окно **Свойства папки** , и закройте проводник Windows.  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a>Связывание нового расширения файла с редактором кода в среде SQL Server Management Studio  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Сервис** выберите **Параметры**.  
  
2.  В диалоговом окне **Параметры** щелкните **Текстовый редактор**, а затем — **Расширение файла**.  
  
3.  В поле **Расширение** введите новое расширение файла.  
  
4.  В поле **Редактор** выберите редактор кода, который хотите использовать для открытия данного типа файлов, нажмите кнопку **Добавить**, а затем кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Программа SSMS](../../tools/sql-server-management-studio/ssms-utility.md)  
  
  
