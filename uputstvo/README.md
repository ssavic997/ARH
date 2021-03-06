Uputstva za instalaciju ASM sintakse
=======================

##1. gedit
###i) Šta je gedit?
Gedit je program za editovanje tekstualnih fajlova koji se već nalazi u Ubuntu distribucijama. Kao i većina drugih programa slične namene ni gedit nema preinstaliranu sintaksu za asembler.
![](http://i.stack.imgur.com/rXTxF.png)

###ii) Podešavanje sintakse
Sa repozitorijuma FTN-a potrebno je preuzeti sledeće fajlove:
[asm.lang](http://www.acs.uns.ac.rs/sr/filebrowser/download/474)
[Overrides.xml](http://www.acs.uns.ac.rs/sr/filebrowser/download/476)

####Za starije verzije sistema:
1. U folder `/usr/share/gtksourceview-2.0/language-specs/` iskopirati fajl [asm.lang](http://www.acs.uns.ac.rs/sr/filebrowser/download/474)
2. Pokrenuti komandu `sudo chmod 664 /usr/share/gtksourceview-2.0/language-specs/asm.lang` kako bi iskopirani fajl dobio potrebne dozvole za rad
3. U folder `/usr/share/mime/packages/` iskopirati fajl [Overrides.xml](http://www.acs.uns.ac.rs/sr/filebrowser/download/476) ukoliko se on već ne nalazi tu, a ukoliko se nalazi potrebno je samo na njega dodati sadržaj ovog fajla
4. Potrebno je i pokrenuti sledeću komandu `sudo update-mime-database /usr/share/mime` kako bi se ažurirala baza mime ekstenzija

####Za novije verzije sistema:
1. U folder `/usr/share/gtksourceview-3.0/language-specs/` iskopirati fajl [asm.lang](http://www.acs.uns.ac.rs/sr/filebrowser/download/474)
2. Pokrenuti komandu `sudo chmod 664 /usr/share/gtksourceview-3.0/language-specs/asm.lang` kako bi iskopirani fajl dobio potrebne dozvole za rad
3. U folder `/usr/share/mime/packages/` iskopirati fajl [Overrides.xml](http://www.acs.uns.ac.rs/sr/filebrowser/download/476) ukoliko se on već ne nalazi tu, a ukoliko se nalazi potrebno je samo na njega dodati sadržaj ovog fajla
4. Potrebno je i pokrenuti sledeću komandu `sudo update-mime-database /usr/share/mime` kako bi se ažurirala baza mime ekstenzija

Nakon ovoga gedit bi trebalo da prepoznaje asemblerske fajlove i da sam uključi odgovarajuću sintaksu, međutim ako to nije slučaj moguće je sintaksu ručno promeniti u donjem desnom uglu


##Sublime
###i) Šta je Sublime?
Sublime Text je višenamenski tekstualni editor koji se lako prilagođava.
![sublime](https://www.sublimetext.com/screenshots/alpha_goto_anything2_large.png)

###ii) Gde skinuti?
Sublime Text može se preuzeti na [zvaničnom sajtu](https://www.sublimetext.com/) i dostupan je u dve verzije 2 i 3 koje se razlikuju po verziji pajtona koju koriste.

###iii) Kako instalirati
#### Windows
Skinuti izvršni fajl sa [sajta](https://www.sublimetext.com/), pokrenuti instalaciju i pratiti uputstva
#### Ubuntu
Skinuti [deb fajl](https://www.sublimetext.com/) u zavisnosti od verzije sistema i samo pokrenuti instalaciju

##iv) Podešavanje sintakse
1. Potrebno je skinuti [Packet Control](https://packagecontrol.io/) za Sublime.
Otvoriti konzolu `Ctrl+~` i zatim nalepiti sledeći tekst i pritisnuti <ENTER>. Sublime mora biti restartovan nakon uspеšne instalacije</br>
Sublime text 2:</br>
`import urllib2,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation') `</br>
Sublime text 3:</br>
`import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by) `</br>
2. Pritiskom na `Ctrl+Shift+P` otvoriće se dijalog sa mogućim komandama gde treba uneti `Install Package` i pritisnuti <ENTER>
3. Nakon nekog vremena izaći će lista svih mogućih ekstenzija. Tu je potrebno pronaći AT&T/GAS sintaksu (najbolje je uraditi pretragu na gasx)
4. Nakon instalacije Sublime bi trebao da otvara asemblerske fajlove sa odgovarajućom sintaksom sam, ali ako to nije slučaj moguće je ovo promeniti u donjem desnom uglu klikom na `AT&T/GAS` sintakse
![](https://raw.githubusercontent.com/calculuswhiz/Assembly-Syntax-Definition/master/screencap/gdb_demo.png)

Uputstva za instalaciju ddd-a
=======================
1. Sa [repozitorijuma](http://www.acs.uns.ac.rs/sr/node/237/178) skinuti ddd za odgovarajuću verziju sistema
2. Pokrenuti deb fajl i započeti instalaciju
3. Ukoliko prilikom pokretanja ne postoje 16-bitni i 8-bitni registri pri vrhu pokrenuti komandu `rm -rf ~/.ddd`