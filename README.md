# react-native-nyt-360-video

This package a port of the popular react-native-video package tweaked to work with 360° videos using the NYT360Video package for iOS. This was done to keep the props the same as react-native-video so that both packages can be used within the same component using the same state variables and props.

Installation
------------

    react-native install react-native-nyt-360-video

Usage
-----

    import Nyt360Video from 'react-native-nyt-360-video';

	-------
	render(){
	    return (
	        <Nyt360Video source={{uri: 'https://video-site.com/my-360-video-url.mp4}}
	        	ref={(ref) => {
	        		this.player = ref
	        	}}
	        	rate={1.0}
	        	volume={1.0}
	        	muted={muted}
	        	paused={!this.state.playing}
	        	repeat={false}
	        	playInBackground={false}
	        	playWhenInactive={false}
	        	progressUpdateInterval={250.0}
	        	onLoadStart={this.loadStart.bind(this)}            
	        	onLoad={this.setDuration.bind(this)}               
	        	onProgress={this.onProgress.bind(this)}               
	        	onEnd={this.onEnd.bind(this)}                      
	        	onError={this.videoError.bind(this)}               
	        	onBuffer={this.onBuffer.bind(this)}                
	        	onTimedMetadata={this.onTimedMetadata.bind(this)}  
	        	style={{}} />
	        )
        }

Known limitations
-----------------

 - Older devices have trouble handling rotation when video width is
   greater than 1920 and occasionally crash
 - Using this in tandem with react-native-camera or other packages that use the gryoscope/accelerometer while the video is playing can occasionally cause a crash (if both packages are trying to read the position of the device at the same time it can cause failure)
 - 360 videos can appear to have a warped effect around the edges of the view, and this can be solved by increasing the transform scale of the video player itself when the video is in landscape mode (to say, `transform: [{scale: this.state.landscape ? 1.2 : 1}]`)

