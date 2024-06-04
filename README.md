# Sinteză marca Eno
Prin intermediul acestui proiect am experimentat cu conceptul de muzică generativă la un nivel amator. O serie de oscilatoare sunt activate, la diferite frecvențe, la variate intervale, aplicând peste acestea o serie de efecte a căror parametrii sunt determinați de gesticulații ale degetelor ce sunt recunoscute folosind TouchDesigner, respectiv modelul MediaPipe antrenat de Google. După ce sunetele sunt generate, iar acestea sunt modificate dinamic de efectele menționate anterior, suma este trimisă înapoi către TouchDesigner, generând pe baza acestora vizuale reactive. Vizualele nu au fost generate pe baza parametrilor preluați de plugin-ul MediaPipe, ci au fost generate pe baza sumei semnalului audio realizate în Pure Data și a fost trimisă către TouchDesigner folosind tool-ul ASIO Link Pro Tool. Alternativ, pentru MacOS, poate fi folosit BlackHole.

#### **Mențiune**
Github nu a permis încărcarea tuturor fișierelor necesare datorită dimensiunilor lor. Astfel, întreaga arhivă a fișierelor necesare rulării integrale a proiectului au fost încărcate la adresa:
[Link text](https://drive.google.com/drive/folders/1d9RhZkud565UBXJyRiBKfEBCfW0GfrL5?usp=sharing)

## Instalare
### Pure Data
A fost folosit Pd-L2Ork, un flavour de Pure Data ce vine preinstalat cu diferite librării ce au fost folosite și în proiectul prezentat.

### MrPeach OSC
Este o librărie de Pure Data ce pune la dispoziție obiecte a căror scop este facilitarea comunicației prin protocolul OSC cu alte programe. Aceasta a fost folosită pentru a comunica date între Pd-L2Ork și TouchDesigner.

### TouchDesigner
TouchDesigner este un mediu de dezvoltare vizuală pentru creația de artă digitală și aplicații multimedia interactive. Utilizat pe scară largă în spectacole live, instalații artistice și vizualizări de date, permite manipularea în timp real a graficii, sunetului și intrărilor variate printr-o interfață nodală intuitivă și flexibilă. În acest proiect, precum a fost menționat a jucat rolul extragerii de parametrii ale gesturilor și generarea de vizuale pe baza sumei muzicale rezultate din Pure Data.

### MediaPipe for TouchDesigner
Mediapipe for TouchDesigner integrează capabilitățile de procesare a datelor vizuale și de urmărire a corpului, mâinilor și feței din Mediapipe în mediul TouchDesigner. Permite dezvoltatorilor să creeze aplicații interactive avansate utilizând recunoașterea și analiza gesturilor în timp real, îmbunătățind astfel experiențele vizuale și performanțele artistice.

### ASIO Link Pro Tool
ASIO Link Pro Tool este un software de interfațare audio care permite rutarea flexibilă și simultană a fluxurilor audio între multiple aplicații și dispozitive ASIO. Ideal pentru studiouri de înregistrare și producție muzicală, optimizează performanțele audio, asigurând latențe scăzute și o calitate superioară a sunetului.

### BlackHole
BlackHole pentru macOS este un driver audio virtual open-source care permite rutarea audio între aplicații fără hardware suplimentar. Utilizatorii pot captura și redirecționa sunetul de la o aplicație la alta, fiind ideal pentru streaming, înregistrări și producție muzicală, cu latență scăzută și calitate audio înaltă.



## (Utilizare)
### Inițializarea plugin-ului MediaPipe for TouchDesigner
Pentru a permite atât recoltarea de date cât și vehicularea acestora prin OSC, trebuie deschis inițial documentul **mediapipe-oscout-reactive.toe**. Recoltarea de date se va activa automat.
### Generarea sunetelor
Pentru a începe generarea sunetelor trebuie deschis fișierul **sinteza_eno_p3_cl_sub_pipo_fingers_2.pd**. Odată ce DSP a fost activat, trebuie activat toggle-ul "Master play" pentru a activa synth-ul. În proximitatea acestui toggle se mai gasesc două bang-uri: unul activează randomizarea timpului de activarea a fiecărei note, iar celălat schimbă armonia notelor generate. 

![Screenshot 2024-06-05 004324](https://github.com/lucagheorghe/PCON-proiect-final/assets/93280965/98577997-fc1b-4f07-a49b-2d4738a5b6a3)

Mâinile trebuie introduse în cadrul camerei de captură secvențial astfel: înâi stânga, apoi dreapta.
Pentru a altera sunetul se va folosi mâna stângă iar efectele sunt dispuse astfel:
- degetul mare: modulație în Amplitudine;
- degetul arătător: ping-pong delay dreapta;
- degetul mijlociu: ping-pong delay time;
- degetul inelar: ping-pong delay stânga;
- degetul mic: modulație în frecvență (momentan dezactivat, încă în stadiu experimental)
În prezent, singurul scop al mâinii drepte este de a activa și dezactiva modificarea efectelor printr-o mișcare de pălmuire în jos. (un fel de edit mode)

![Screenshot 2024-06-05 004817](https://github.com/lucagheorghe/PCON-proiect-final/assets/93280965/5323a6b8-d64d-43b5-b054-0f6559a65ded)

Mai departe, pentru a permite audiția și totodată comunicarea sumei către TouchDesigner pentru a genera vizuale reactive, setarea de output audio din Pure Data trebuie făcută pe același driver ca cel de Audio Device In din TouchDesigner. Mai departe, vizualele reactive pot fi observate în TouchDesigner.

![Screenshot 2024-06-05 004447](https://github.com/lucagheorghe/PCON-proiect-final/assets/93280965/73fcc56c-895c-412b-963a-a4a31f9372ca)

![Screenshot 2024-06-05 004535](https://github.com/lucagheorghe/PCON-proiect-final/assets/93280965/37bc6ee5-1e86-44c6-b1dc-68d834b55323)

## (Istoric)

(24-04) Dezvoltarea patch-ului generativ în TouchDesigner și experimentarea efectelor ce vor urma să fie implementate + dezvoltarea patch-ului de TouchDesigner ce recoltează date ale gesturilor.

(24-05) Dezvoltarea subpatch-urilor de vehiculare a datelor dintre TouchDesigner și Pure Data.

(24-06) Finisarea proiectului și dezvoltarea rețelei de audio-video din TouchDesigner.

## (Link-uri)
[Link text](https://puredata.info/downloads/Pd-L2Ork)
[Link text](https://github.com/pd-externals/mrpeach)
[Link text](https://derivative.ca/download)
[Link text](https://github.com/torinmb/mediapipe-touchdesigner)
[Link text](https://give.academy/downloads/2018/03/03/ODeusASIOLinkPro/)
[Link text](https://existential.audio/blackhole/)

# Dezvoltarea proiectului

Pentru început:

1. Creează-ți cont pe Github
2. Download și install [Github Desktop](https://desktop.github.com/)
3. Citește [acest ghid](https://charlesmartin.com.au/blog/2020/08/09/student-project-repository) și ține la îndemână [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet).

Apoi, procesul este următorul (inspirat de [aici](https://cs.anu.edu.au/courses/comp1720/deliverables/05-major-project/#submission-process)):

1. *fork* al acestui template către propriul tău cont de Github

![](assets/fork.gif)

_(dacă preferi cumva ca repo-ul să nu fie vizibil de către public, îl poți seta ca Private din Settings - "Change visibility". Atunci trebuie să mă adaugi drept colaborator, ca eu să am acces.)_

2. *clone* al repo-ului din Github Desktop pentru a-l downloada local

![](assets/clone.gif)

3. *commit* și *push* pe măsură ce lucrezi la proiect. Ultima versiune push-ată pe server înainte de deadline va conta pentru evaluare.

![](assets/commit.gif)

## Elemente obligatorii

1. Acest readme completat. Titlu, descriere, mod de utilizare, istoric, link-uri utile.

   Poți include și imagini și chiar [gif-uri animate](https://www.screentogif.com/), sau link-uri către materiale audio/video.
   
   Vezi [aici](https://charlesmartin.com.au/blog/2020/08/09/student-project-repository) mai multe sugestii.

2. [Declarația de originalitate](statement-of-originality.yml) completată. Tot ce nu este inclus acolo va fi considerat 100% contribuție proprie.

    *(formatul este adaptat de [aici](https://gitlab.cecs.anu.edu.au/comp1720/2018/comp1720-2018-major-project/-/blob/master/statement-of-originality.yml). Da, este un pic ironic să refolosim un doc [de altundeva](https://cs.anu.edu.au/courses/comp1720/resources/faq/#how-do-i-fill-out-my-statement-of-originality), dar menționăm sursa deci nu este plagiat!)*

3. Proiectul în sine. Tot codul trebuie să fie prezent, proiectul trebuie să poată rula conform instrucțiunilor din readme. Dacă e nevoie de asset-uri mari (sunete, video etc), [folosește Git LFS](https://git-lfs.github.com/) sau include link de download în instrucțiunile de instalare.

