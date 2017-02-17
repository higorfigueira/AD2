#include <stdio.h>
#include <stdlib.h>

typedef struct no{
    int info;
    struct no *esq;
    struct no *dir;
}no;

int main()
{
    no *t = NULL;
    int x;
    printf("Informe um numero:\n");
    scanf("%d", &x);

    inserir(&t, x);
    preOrdem(t);

    return 0;
}

void inserir (no **t, int x){
    if(*t == NULL){
        no *novo = (no*)malloc(sizeof(no));
        novo->info = x;
        novo->dir = novo->esq = NULL;
        *t = novo;
    }
    else {
        no *aux = *t;
        if(x < aux->esq)
            inserir(&(aux->esq), x);
        else
            inserir(&(aux->dir), x);
    }
}

void preOrdem (no *t){
    if(t!=NULL){
        printf("\n%d\n", t->info);
        preOrdem(t->esq);
        preOrdem(t->dir);
    }
}






