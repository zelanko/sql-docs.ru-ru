---
title: 'HelloData: Простое приложение ADO | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- HelloData sample application [ADO]
- ADO, samples
ms.assetid: de4bcd56-dac2-45e6-95ab-9fd7f25878fc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e666f479d95e3915703dc539ba2731e95175488b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925131"
---
# <a name="hellodata-a-simple-ado-application"></a>HelloData: простое приложение ADO
Это простое приложение пошаговые инструкции по каждой из четырех основных операций ADO: получение, анализ, редактирование и обновление данных. Эти операции выполняются в образце базы данных "Борей", в состав Microsoft® SQL Server. Чтобы сосредоточиться на основ ADO и предотвратить перегруженность кода, обработка ошибок в примере сводится к минимуму.  
  
### <a name="to-run-hellodata"></a>Для запуска HelloData  
  
1.  Создайте новый проект Standard exe-файла Visual Basic, который ссылается на библиотеки ADO. Дополнительные сведения см. в разделе [ссылки на библиотеки ADO](../../../ado/guide/referencing-the-ado-libraries.md).  
  
2.  Создайте четыре кнопки в верхней части формы, установка **имя** и **заголовок** свойства значения, показанные в таблице в конце этого раздела.  
  
3.  Ниже кнопок Добавить **элемента управления DataGrid в Microsoft** (Msdatgrd.ocx). Файл Msdatgrd.ocx входит в состав Visual Basic и находится в каталоге \windows\system32 или \winnt\system32. Чтобы добавить элемент управления DataGrid в область элементов Visual Basic, выберите **компонентов...**  из **проекта** меню. Затем установите флажок рядом с элементом «элемент управления DataGrid Microsoft 6.0 (SP3) (OLE DB)» и нажмите кнопку **ОК**. Добавление элемента управления в проект, перетащите элемент управления DataGrid с панели инструментов в Visual Basic форму.  
  
4.  Создание **TextBox** формы под сеткой и задать его свойства, как показано в таблице. Когда вы закончите форме должно выглядеть как следующий рисунок.  
  
5.  Наконец, скопируйте код, указанный в [код HelloData](../../../ado/guide/data/hellodata-code.md)и вставьте его в окне редактора кода формы. Нажмите клавишу **F5** для выполнения кода.  
  
> [!NOTE]
>  В следующем примере и в руководстве идентификатор пользователя «MyId» с паролем «123абв» используется для проверки подлинности на сервере. Следует заменить эти значения, используя действительные учетные данные для сервера. Кроме того замените значение «MySQLServer» с именем сервера.  
  
 Подробное описание кода, см. в разделе [комментарии к hellodata](../../../ado/guide/data/comments-on-hellodata.md).  
  
 ![Показывает форму Form1 для приложения HelloData VB](../../../ado/guide/data/media/hellodata.gif "HelloData")  
  
|Тип элемента управления|Свойство|Значение|  
|------------------|--------------|-----------|  
|Формы|Имя|Form1|  
||Высота|6500|  
||Ширина|6500|  
|MS DataGrid|Name|grdDisplay1|  
|TextBox|Имя|txtDisplay1|  
||Многострочный|true|  
|Кнопка команды|Name|cmdGetData|  
||Заголовок|Получение данных|  
|Кнопка команды|Name|cmdExamineData|  
||Заголовок|Изучение данных|  
|Кнопка команды|Name|cmdEditData|  
||Заголовок|Изменение данных|  
|Кнопка команды|Name|cmdUpdateData|  
||Заголовок|Обновление данных|
