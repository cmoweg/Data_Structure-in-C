[toc]

# 단일 연결리스트

```c++
#pragma warning(disable:4996)
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

typedef struct NODE { char name[21]; int grade; struct NODE *next; } NODE;

NODE *getnode(char *name, int grade) {

	NODE *newnode = (NODE *)malloc(sizeof(NODE));

	newnode->next = NULL;

	strcpy(newnode->name, name);

	newnode->grade = grade;

	return newnode;

}



int main() {

	char name[21];

	int grade;

	NODE *L = NULL, *newnode;

	NODE*ptr, *tmp;

	while (1) {

		// name 입력받고 0이면 break;

		//제일 처음이면 L== NULL일 것.
		gets_s(name);
		if (strcmp(name, "0") == 0) break;
		scanf("%d", &grade);
		getchar();
		if (L == NULL) L = getnode(name, grade);

		else {

			newnode = getnode(name, grade);

			newnode->next = L;

			L = newnode;
		}
	}

	for (ptr = L; ptr != NULL; ptr = ptr->next) {
		printf("%s %d", ptr->name, ptr->grade);
	}


	for (ptr = L; ptr != NULL; ) {

		tmp = ptr->next;

		free(ptr);

		ptr = tmp;

	}


	return 0;
}
```

