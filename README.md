#include <stdio.h>

int main()
{
  int set1[100], set2[100], set3[100], flag, op, num1, num2, k = 0;
  printf("Enter the Count the element in set 1:\n");
  scanf("%d", &num1);
  printf("Enter the elements of set 1:\n");
  for (int i = 0; i < num1; i++)
  {
    scanf("%d", &set1[i]);
  }
  printf("Enter the Count the element in set 2:\n");
  scanf("%d", &num2);
  printf("Enter the elements of set 2:\n");
  for (int i = 0; i < num2; i++)
  {
    scanf("%d", &set2[i]);
  }
  printf("Set A:: { ");
  for (int i = 0; i < num1; i++)
  {
    printf("%d ", set1[i]);
  }
  printf("}\n");
  printf("Set B:: { ");
  for (int i = 0; i < num2; i++)
  {
    printf("%d ", set2[i]);
  }
  printf("}\n");
repeat:
  printf("\n \n Select the operation.\n 1. Union \n 2. Intersection \n 3. Difference \n 4. Symmetric Difference \n 5.Exit \n\n\n");
  scanf("%d", &op);
 

  if (op == 1)
  {
    for (int i = 0; i < num1 + num2; i++)
    {
      set3[i] = 0;
    }
    for (int i = 0; i < num1; i++)
    {
      set3[i] = set1[i];
      k++;
    }

    for (int i = 0; i < num2; i++)
    {
      flag = 0;
      for (int j = 0; j < num1; j++)
      {
        if (set1[j] == set2[i])
        {
          flag = 1;
          break;
        }
      }
      if (flag == 0)
      {
        set3[k] = set2[i];
        k++;
      }
    }
    printf(" \n Set union (A U B) is : { ");
    for (int i = 0; i < k; i++)
    {
      printf("%d ", set3[i]);
    }
    printf("}");
    goto repeat;
  }

  else if (op == 2)
  {
    printf("Intersection of A and B is : { ");
    for (int i = 0; i < num2; i++)
    {
      flag = 0;
      for (int j = 0; j < num1; j++)
      {
        if (set1[j] == set2[i])
        {
          flag = 1;
        }
      }
      if (flag == 1)
      {
        printf("%d ", set2[i]);
      }
    }
    printf("}");
     goto repeat;
  }

  else if (op == 3)
  {
    printf("The Differnce in Set A and B is (A-B) : { ");
    for (int i = 0; i < num1; i++)
    {
      flag = 0;
      for (int j = 0; j < num2; j++)
      {
        if (set1[i] == set2[j])
        {
          flag = 1;
          break;
        }
      }
      if (flag == 0)
      {
        printf("%d ", set1[i]);
      }
    }
    printf("}\n");
    printf("The Difference in Set B and A is (B-A) : { ");
    for (int i = 0; i < num2; i++)
    {
      flag = 0;
      for (int j = 0; j < num1; j++)
      {
        if (set1[j] == set2[i])
        {
          flag = 1;
          break;
        }
      }
      if (flag == 0)
      {
        printf("%d ", set2[i]);
      }
    }
    printf("}\n");
     goto repeat;
  }

  else if (op == 4)
  {
    printf("The Symmetric Differnce in Set A and B is ((A-B) U (B-A)) :\n{ ");
    for (int i = 0; i < num1; i++)
    {
      flag = 0;
      for (int j = 0; j < num2; j++)
      {
        if (set1[i] == set2[j])
        {
          flag = 1;
          break;
        }
      }
      if (flag == 0)
      {
        printf("%d ", set1[i]);
      }
    }

    for (int i = 0; i < num2; i++)
    {
      flag = 0;
      for (int j = 0; j < num1; j++)
      {
        if (set1[j] == set2[i])
        {
          flag = 1;
          break;
        }
      }
      if (flag == 0)
      {
        printf("%d ", set2[i]);
      }
    }
    printf("}\n");
     goto repeat;
  }
 
   else if(op==5)
   {
     printf("Thank you!\n");
      goto end;
   }
  else
  {
    printf("Enter correct choice \n\n");
    goto repeat;
  }
   end:
   return 0;
}
