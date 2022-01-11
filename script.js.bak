/*Slideshow*/
	
var slideIndex = 1;

function change_slide(n) {show_slide(slideIndex += n);}

function current_slide(n) {show_slide(slideIndex = n);}
	
function show_slide(n)
{
	var i;
	var slides = document.getElementsByClassName("slides");
	var dots = document.getElementsByClassName("dot");
		
	if(n > slides.length) {slideIndex = 1;}
	if(n < 1) {slideIndex = slides.length;}
		
	for(i = 0; i < slides.length; i++)
	{
		slides[i].style.display = "none";
	}
		
	for(i = 0; i < dots.length; i++)
	{
		dots[i].className = dots[i].className.replace(" active", "");
	}
	slides[slideIndex - 1].style.display = "block";
	dots[slideIndex - 1].className += " active";
}
	
show_slide(slideIndex);


/*Audio Player*/
	
//Variables and Functions
let audio = document.getElementById('pl');
let progress_bar = document.getElementById('seek');
let progress_bar_clicked = false;
let volume = document.getElementById('volume-slider');
let play_button = document.getElementById('play');
let song_paused = true;
let volume_icon = document.getElementById('volume-icon');
let mute = false;
let save_volume = 33;

function change_icon()
{
	if(audio.volume === 0) {volume_icon.src = "volume-0.png";}
	if(audio.volume > 0 && audio.volume <= 0.33) {volume_icon.src = "volume-1.png";}
	if(audio.volume > 0.33 && audio.volume <= 0.66) {volume_icon.src = "volume-2.png";}
	if(audio.volume > 0.66 && audio.volume <= 1) {volume_icon.src = "volume-3.png";}
}

//Play and Pause buttons
play_button.onclick = function()
{
	if(song_paused == true)
	{
		audio.play();
		song_paused = false;
		play_button.style.background = "url(pause.png)";
	}
	else
	{
		audio.pause();
		song_paused = true;
		play_button.style.background = "url(play.png)";
	}
}

//Progress bar
audio.onloadedmetadata = function(){
	progress_bar.max = audio.duration;
	//progress_bar_clicked = false;
	
	//Volume icon when starting the page
	audio.volume = volume.value / 100;
	change_icon();	
}

audio.ontimeupdate = function() {
	if(progress_bar_clicked == false) {progress_bar.value = audio.currentTime;}
}

progress_bar.onmousedown = function() {
	audio.pause();
	progress_bar_clicked = true;
}
progress_bar.onmouseup = function() {
	if(song_paused == false) {audio.play();} 
	progress_bar_clicked = false;
}

progress_bar.onclick = function(event){
		audio.currentTime = progress_bar.value;
}

//Volume icon

volume_icon.onmousedown = function() {
	if(mute == false)
	{
		mute = true;
		save_volume = volume.value;
		volume.value = 0;
		audio.volume = 0;
		volume_icon.src = "volume-0.png";
	}
	else
	{
		mute = false;
		if(save_volume != 0)
		{
			volume.value = save_volume;
			audio.volume = volume.value / 100;
			change_icon();
		}
	}
}

//Volume slider

volume.oninput = function() {
	audio.volume = volume.value / 100;
	mute = false;
	
	if(audio.volume === 0) {volume_icon.src = "volume-0.png"; mute = true;}
	if(audio.volume > 0 && audio.volume <= 0.33) {volume_icon.src = "volume-1.png";}
	if(audio.volume > 0.33 && audio.volume <= 0.66) {volume_icon.src = "volume-2.png";}
	if(audio.volume > 0.66 && audio.volume <= 1) {volume_icon.src = "volume-3.png";}
}