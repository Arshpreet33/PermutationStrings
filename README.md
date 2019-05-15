# PermutationStrings
Find all permutation strings related to input string


Sample Test code in c#

using System;

public class Test
{
	public static void Main()
	{
		string s = "ram";
		TestingCode(s);
		
	}
	private static void PrintLast2Char(char []c, char a, char b)
	{
		Console.Write(c[a]+ c[b]);
		Console.Write(c[b]+ c[a]);
	}
	private static void WorkingCode(string s)
	{
		
		char []c2 = s.ToCharArray();
		for(int j = 0; j < c2.Length; j++)
		{
			Console.Write(c2[j]);
			char []c = s.Substring(j+1, c2.Length-1).ToCharArray();
			for(int i = 0; i < c.Length; i++)
			{
				Console.Write(c[i]);
				Console.Write(c[(i + 1) % c.Length]);
				Console.Write(c[(i + 2) % c.Length]);
				Console.WriteLine();
				
				Console.Write(c[i]);
				Console.Write(c[(i + 2) % c.Length]);
				Console.Write(c[(i + 1) % c.Length]);
				Console.WriteLine();
			}
		}
	}
	private static int GetFactorial(int a)
	{
		int p = 1;
		for(int i = a; i > 0 ; i--)
		{
			p = p * i;
		}
		return p;
	}
	private static void TestingCode(string s)
	{
		char[] c =s.ToCharArray();
		char[,] c2 = new char[GetFactorial(c.Length),c.Length];
		
		for(int i = 0; i < c.Length; i++)
		{
			if(c.Length - i <= 2)
			for(int j = (i * (GetFactorial(c.Length - 1))); j < ((i + 1) * (GetFactorial(c.Length - 1))); j++)
			{
				c2[j,i] = c[i];
			}
		}
		//Print the output.
		for(int i = 0; i < GetFactorial(c.Length); i++)
		{
			for(int j = 0; j < c.Length; j++)
			{
				Console.Write(c2[i,j]);
			}
			Console.WriteLine();
		}
	}
}
