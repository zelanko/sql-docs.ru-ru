---
title: Окно сообщения об исключении программы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 316afc6d5f3a87ff7431240681066ac5ee66ede6
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60157940"
---
# <a name="program-exception-message-box"></a>Выведение окна сообщения об исключении программы
  Можно воспользоваться окном сообщения об исключении в приложениях, чтобы предоставить значительно больше возможностей управления информированием, чем в классе <xref:System.Windows.Forms.MessageBox>. Дополнительные сведения см. в разделе [программирования поле сообщение исключение](../../../2014/database-engine/dev-guide/exception-message-box-programming.md). Сведения о том, как получить и развернуть библиотеку DLL окна сообщений об исключениях, см. в разделе [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a>Обработка исключения с помощью окна сообщения об исключении  
  
1.  Добавьте в проект управляемого кода ссылку на сборку Microsoft.ExceptionMessageBox.dll.  
  
2.  (Необязательно) Добавить `using` (C#) или `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET) директиву, чтобы использовать <xref:Microsoft.SqlServer.MessageBox> пространства имен.  
  
3.  Создайте блок try-catch для обработки ожидаемого исключения.  
  
4.  В блоке `catch` создайте экземпляр класса <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>. Передайте <xref:System.Exception> объект, обрабатываемый `try` - `catch` блока.  
  
5.  (Необязательно) Задайте одно или несколько из следующих свойств <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> Перечисление, указывающее кнопки для отображения в окне сообщения об исключении.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> Перечисление, указывающее кнопку по умолчанию для окна сообщения об исключении.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> Перечисление, используемое для управления другими аспектами поведения окна сообщения об исключении.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> Перечисление, указывающее символ для отображения в окне сообщения об исключении.  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>. Передайте родительское окно, к которому относится окно сообщения об исключении.  
  
7.  Отметьте возвращаемое значение перечисления <xref:System.Windows.Forms.DialogResult>, если требуется определить, какую кнопку нажал пользователь (необязательно).  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a>Отображение окна сообщения об исключении без самого исключения  
  
1.  Добавьте в проект управляемого кода ссылку на сборку Microsoft.ExceptionMessageBox.dll.  
  
2.  (Необязательно) Добавить `using` (C#) или `Imports` директивы (Visual Basic .NET) для использования <xref:Microsoft.SqlServer.MessageBox> пространства имен.  
  
3.  Создайте экземпляр класса <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> . Передайте текст сообщения как <xref:System.String>.  
  
4.  (Необязательно) Задайте одно или несколько из следующих свойств <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> Перечисление, указывающее кнопки для отображения в окне сообщения об исключении.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> — заголовок диалогового окна для окна сообщения об исключении.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> Перечисление, указывающее кнопку по умолчанию для диалогового окна сообщения об исключении.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> Перечисление, используемое для управления другими аспектами поведения окна сообщения об исключении.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> Перечисление, указывающее символ для отображения в окне сообщения об исключении.  
  
5.  Вызовите метод <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>. Передайте родительское окно, к которому относится окно сообщения об исключении.  
  
6.  (Необязательно) Какую из кнопок нажал пользователь, можно определить, проверив значение возвращенного перечисления <xref:System.Windows.Forms.DialogResult>.  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a>Отображение окна сообщения об исключении с пользовательскими кнопками  
  
1.  Добавьте в проект управляемого кода ссылку на сборку Microsoft.ExceptionMessageBox.dll.  
  
2.  (Необязательно) Добавить `using` (C#) или `Imports` директивы (Visual Basic .NET) для использования <xref:Microsoft.SqlServer.MessageBox> пространства имен.  
  
3.  Создайте экземпляр класса <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> одним из двух следующих способов.  
  
    -   Передайте <xref:System.Exception> объект, обрабатываемый `try` - `catch` блока.  
  
    -   Передайте текст сообщения как <xref:System.String>.  
  
4.  Установите одно из следующих значений для свойства <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A>.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore> — Отображает **прервать**, **повторите**, и **пропустить** кнопки.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> — отображает пользовательские кнопки.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK> — Отображает **ОК** кнопки.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel> — Отображает **ОК** и **отменить** кнопки.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel> — Отображает **повторите** и **отменить** кнопки.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo> — Отображает **Да** и **нет** кнопки.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel> — Отображает **Да**, **нет**, и **отменить** кнопки.  
  
5.  При использовании пользовательских кнопок вызовите один из перегруженных методов <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A>, чтобы указать текст для пользовательских кнопок, количество которых не более пяти (необязательно).  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>. Передайте родительское окно, к которому относится окно сообщения об исключении.  
  
7.  (Необязательно) Какую из кнопок нажал пользователь, можно определить, проверив значение возвращенного перечисления <xref:System.Windows.Forms.DialogResult>. При использовании пользовательских кнопок отметьте значение объекта <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> для свойства <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A>, чтобы определить, какую пользовательскую кнопку нажал пользователь.  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a>Как разрешить пользователям показывать или не показывать окно сообщения об исключении  
  
1.  Добавьте в проект управляемого кода ссылку на сборку Microsoft.ExceptionMessageBox.dll.  
  
2.  (Необязательно) Добавить `using` (C#) или `Imports` директивы (Visual Basic .NET) для использования <xref:Microsoft.SqlServer.MessageBox> пространства имен.  
  
3.  Создайте экземпляр класса <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> одним из двух следующих способов.  
  
    -   Передайте <xref:System.Exception> объект, обрабатываемый `try` - `catch` блока.  
  
    -   Передайте текст сообщения как <xref:System.String>.  
  
4.  Задайте для свойства <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> значение `true`.  
  
5.  Укажите текст с вопросом пользователю, показывать ли снова окно сообщения об исключении, для свойства <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A> (необязательно). По умолчанию используется текст «Не показывать больше это сообщение».  
  
6.  Если требуется сохранять принятое пользователем решение лишь на протяжении выполнения приложения, присвойте значение свойства <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> глобальной переменной <xref:System.Boolean>. Вычислите это значение перед созданием экземпляра окна сообщения об исключении.  
  
7.  Если необходимо постоянно хранить принятое пользователем решение, выполните следующее.  
  
    1.  Вызовите метод CreateSubKey, чтобы открыть используемый вашим приложением пользовательский раздел реестра, и задайте значение <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A>, равное возвращаемому объекту.  
  
    2.  Установите в свойстве <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> имя используемого значения реестра.  
  
    3.  Присвойте параметру <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> значение `true`.  
  
    4.  Вызовите метод <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>. Вычисляется указанный раздел реестра, и окно сообщения об исключении отображается только тогда, когда хранящиеся в разделе реестра данные равны 0. Если же отображается диалоговое окно и пользователь устанавливает флажок до нажатия кнопки, то данным в разделе реестра присваивается 1.  
  
## <a name="example"></a>Пример  
 В этом примере используется окно сообщения об исключении только с кнопкой **ОК** , чтобы отобразить сведения из исключения приложения, которые включают в себя обрабатываемое исключение и дополнительную информацию, отражающую специфику данного приложения.  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a>Пример  
 В этом примере используется окно сообщения об исключении с кнопками **Да** и **Нет** , одну из которых выбирает пользователь.  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a>Пример  
 В этом примере используется окно сообщения об исключении с пользовательскими кнопками.  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a>Пример  
 В этом примере используется флажок для определения того, показывать ли окно сообщения об исключении.  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a>Пример  
 В этом примере используется флажок и раздел реестра для определения того, показывать ли окно сообщения об исключении.  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a>Пример  
 В этом примере используется окно сообщения об исключении для отображения дополнительных сведений, полезных при диагностике и устранении неполадок.  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  
