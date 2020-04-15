---
title: Создание почтовых этикеток в Microsoft Word с использованием визуальных данных FoxPro (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data [ODBC], mailing labels
- Visual FoxPro data [ODBC], Word
- mailing labels [ODBC]
- Visual FoxPro ODBC driver [ODBC], Word
- FoxPro ODBC driver [ODBC], word
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3ca6c729cfa988e2560192d705bc24e9e7b4fa1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280804"
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>Создание почтовых наклеек в Microsoft Word с использованием данных Visual FoxPro
Вы можете использовать визуальные данные FoxPro в документе Microsoft Word для Windows 95 или Windows 98. Например, можно создать почтовые метки из информации о клиентах, хранящейся в таблице Visual FoxPro.  
  
### <a name="to-create-mailing-labels"></a>Создание почтовых меток  
  
1.  В Microsoft Word создайте новый пустой документ.  
  
2.  Из меню Инструменты выберите Mail Merge.  
  
3.  В Справке по слиянию почты выберите «Создание», а затем выберите почтовые метки.  
  
4.  В главном документе выберите Active Window.  
  
5.  Под source data выберите Get Data, а затем выберите Источник открытых данных.  
  
6.  В диалоговом окне исхода открытых данных выберите MS Query.  
  
7.  В диалоговом окне Select Data Source выберите источник данных Visual FoxPro, а затем нажмите «Использование».  
  
8.  Если база данных, доступ к ней имеет источник данных, включает таблицы, выберите таблицу из диалогового окна Add Tables. Запрос Майкрософт отображает добавленную таблицу в верхней половине конструктора запросов.  
  
9. Выберите поля для запроса, перетащив их из таблицы на нижнюю половину конструктора.  
  
10. Из меню файла выберите Return Data в Microsoft Word. Запрос Майкрософт закрывается, и выбранные данные доступны для использования в документе слияния почты.  
  
11. В соответствии с основным документом выберите настройку.  
  
12. В диалоговом поле Label Options выберите нужный принтер и пометьте информацию, а затем нажмите OK.  
  
13. В диалоговом окне Create Labelвы выберите поля, которые вы хотите распечатать на почтовых метки, а затем нажмите OK.  
  
14. В Справке по слиянию почты, под слиянием данных с документом, нажмите Merge.  
  
15. В поле диалога слияния выберите параметры, которые вы хотите, а затем нажмите Merge.
