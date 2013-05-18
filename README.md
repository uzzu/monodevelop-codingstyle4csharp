MonoDevelop CodingPolicy File(C#)
====
MonoDevelopにはコードフォーマッターが搭載されています。

* フォーマットを適用したいファイルを開いて、``編集->フォーマット->ドキュメントをフォーマット``で適用されます。
    * キーボードショートカットを設定しておくと良いですね。
        1. ``MonoDevelop(Unityの場合はMonoDevelop-Unity) -> Preference...``でMonoDevelopオプションを開く
        2. ``設定 -> キーバインディング``で右側に出てきたウィンドウの一番下に、編集の項目があり、ここに``ドキュメントをフォーマット``があるのでこれをよしなに設定しましょう

MonoDevelopではコードフォーマッターの設定はExport、Importできます。  
しかしながらデフォルトのコードフォーマッターの設定がなんだかC#っぽくないので、  
設定を修正してExportしました。  
CodingStyleForCSharp.mdpolicyをImportして使ってください。  

# How to import?
1. ``MonoDevelop(Unityの場合はMonoDevelop-Unity) -> Custom Policies...``でMonoDevelopオプションを開く
2. 右上のボタンの``Add Policy -> From file...``でCodingStyleForCSharp.mdpolicyを開く
3. 右上のボタンの``Export -> To project or solution...``で、設定を取り込みたいソリューション(プロジェクト)を選択する
4. ソリューションビューのプロジェクトを右クリックして、ソリューション(プロジェクト)オプションを開く
5. ``ソースコード -> コードフォーマッティング``を選択し、右に出てきたファイル種別のうち、  
    以下のファイル種別にCodingStyleForCSharpを適用する。
    * C#ソースコード
    * Text file
    * XMLドキュメント
6. フォーマッタを適用してみる。適用されてるのを確認しましょう。適用されていたら終わりです。お疲れ様でした。

# How to export?
1. ``MonoDevelop(Unityの場合はMonoDevelop-Unity) -> Custom Policies...``でMonoDevelopオプションを開く
2. 右上のボタンの``Add Policy -> From project or solution...``で、設定内容をExportしたいソリューション(プロジェクト)を選択する
3. 右上のボタンの``Export -> To file...``でファイル名指定してExportします。お疲れ様でした。

# Settings
* ハードタブ
* ブロック構文は改行且つインデント、但しプロパティ宣言時のGet, Set及びイベント宣言時のAdd, Removeは1行記述を許容
* and more...(詳しくはCode examplesを参考にしてください)

## Code examples
* フォーマット例はEdit Profileで閲覧が可能ですが、一例をここに記載します。

### Blank lines
```csharp
using System;
using System.Collections;

namespace TestSpace
{
	using MyNamespace;

	class Test
	{
		int a;
		string b;

		public Test(int a, string b)
		{
			this.a = a;
			this.b = b;
		}

		void Print()
		{
			Console.WriteLine("a: {0} b : {1}", a, b);
		}
	}

	class MyTest
	{
	}
}
```
### General syntax blocks
```csharp
class ClassDeclaration
{ 
	public void TestMethod()
	{
		try
		{
			TestMethod("");
		}
		catch (Exception e)
		{
			// Do something
		}
		finally
		{
			// Do something
		}
	}
		
	public void TestMethod(string test)
	{
		lock (this)
		{
			switch (test)
			{
				case "A":
					Console.WriteLine("was A");
					break;
				case "B":
					Console.WriteLine("was B");
					break;
			}
		}
	}
		
	public void Calculate(int a, int b)
	{
		if (a < b)
		{
			for (int i = a; i < b; i++)
			{
				Console.WriteLine(i);
			}
		}
		else
		{
			using (object o = new object ())
			{
				while (b < a)
				{
					ConentryNamesole.WriteLine(b++);
				}
			}
		}
	}
}
```

### Events
```csharp
class ClassDeclaration
{
	EventHandler<EventArgs> onAction;

	public event EventHandler<EventArgs> Action
	{
		add { onAction = (EventHandler<EventArgs>) Delegate.Combine(onAction, value); }
		remove { onAction = (EventHandler<EventArgs>) Delegate.Remove(onAction, value);}
	}

	EventHandler<EventArgs> onAnotherAction;

	public event EventHandler<EventArgs> AnotherAction
	{
		add
		{
			if (value != null)
			{
				onAnotherAction = (EventHandler<EventArgs>) Delegate.Combine(onAnotherAction, value);
			}
		}
		remove
		{
			if (value != null)
			{
				onAnotherAction = (EventHandler<EventArgs>) Delegate.Remove(onAnotherAction, value);
			}
		}
	}
}
```

