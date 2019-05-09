# Enigme
#include<stdio.h>
#include<string.h>
#include"enigme.h"
#include "SDL/SDL.h"
#include <SDL/SDL_image.h>
#include <SDL/SDL_mixer.h>
#include<SDL/SDL_ttf.h>
/**
*@file enigme.c
* @brief testing
* @ author respawnables
*@ version 1 
*/
 void functionenigme( SDL_Surface *screen){
SDL_Surface *answer=NULL,*enigme=NULL;
SDL_Rect posanswer,posenigme;
SDL_Event event;
Mix_Chunk *sound;
sound=Mix_LoadWAV("correct.wav");
int done=1;
posenigme.x=699;
posenigme.y=14;
enigme=IMG_Load("enigme1.png");
SDL_BlitSurface(enigme,NULL,screen,&posenigme);
SDL_Flip(screen);

while(done)
{  while(SDL_PollEvent(&event)){
  switch (event.type)
  {case SDL_KEYDOWN:
    if (event.key.keysym.sym == SDLK_a)
    { answer=IMG_Load("wronganswer.png");
      posanswer.x=699;
      posanswer.y=293;
      SDL_BlitSurface(answer,NULL,screen,&posanswer);
      SDL_Flip(screen);
      Mix_PlayChannel(-1,sound,0);
       SDL_Delay(1000);
       done=0;
    }
    if (event.key.keysym.sym == SDLK_b)
    {answer=IMG_Load("wronganswer.png");
      posanswer.x=699;
      posanswer.y=358;
      SDL_BlitSurface(answer,NULL,screen,&posanswer);
      SDL_Flip(screen);
      Mix_PlayChannel(-1,sound,0);
       SDL_Delay(1000);
       done=0;
    }
    if (event.key.keysym.sym == SDLK_c)
    {sound=Mix_LoadWAV("correct.wav");
    Mix_PlayChannel(-1,sound,0);
      answer=IMG_Load("rightanswer.png");
      posanswer.x=699;
      posanswer.y=423;
      SDL_BlitSurface(answer,NULL,screen,&posanswer);
      SDL_Flip(screen);

       SDL_Delay(1000);
      done=0;
    }
    if (event.key.keysym.sym == SDLK_d)
    {answer=IMG_Load("wronganswer.png");
      posanswer.x=699;
      posanswer.y=488;
      SDL_BlitSurface(answer,NULL,screen,&posanswer);
      SDL_Flip(screen);
      Mix_PlayChannel(-1,sound,0);
       SDL_Delay(1000);
       done=0;
    }

}
}}
Mix_FreeChunk(sound);
SDL_FreeSurface(answer);
SDL_FreeSurface(enigme);
}
