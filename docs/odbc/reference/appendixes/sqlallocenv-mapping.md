---
title: СЗЛАллокЕнВ Картирование (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb26e3443fabda2d6490c071b1f2668895e66b8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304045"
---
# <a name="sqlallocenv-mapping"></a>Сопоставление SQLAllocEnv
Когда приложение вызывает **S'LAllocEnv** через драйвер ODBC *3.x,* вызов в **S'LAllocEnv***(phenv)* отображается в **S'LAllocHandle** следующим образом:  
  
1.  Менеджер драйвера выделяет ручку среды и возвращает ее в приложение. Менеджер драйвера вызывает **S'LSetEnvAttr,** чтобы настроить атрибут SQL_ATTR_ODBC_VERSION среды на SQL_OV_ODBC2.  
  
2.  Когда приложение устанавливает первое соединение с водителем, менеджер драйвера вызывает  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     в драйвере с *OutputHandlePtr* установлен на *phenv*.
