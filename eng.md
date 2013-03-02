# Environmental Design with the Device API

If you’ve ever stood on a chair holding a cell phone up to get a better signal or refreshed a page that’s been hanging for 30 seconds, you already know that today’s user experiences have a gaping hole. We’re spending thousands of hours crafting interfaces that are the product of countless conversations, user tests, and analytics data piled up to our (virtual) eyeballs—only to have the experience crippled by a weird signal coming from a cell tower.

Maybe your user has switched from 3G to WiFi. Maybe her battery is low. Or maybe it’s simply dark out. Whatever the scenario, real-life factors can easily thwart your best intentions—and leave your users frustrated and angry.

The concept of considering real-world factors while designing isn’t new. Environmental design can be traced back to at least 500 BCE, when the ancient Greeks started creating houses that were heated with solar energy, and it’s based on two simple truths: The real world exists, and you can’t control it.

You can’t control all the factors when a user interacts with your design, but you can certainly plan for them simply by acknowledging that they exist. I call these design conditions. Some design conditions, like the device a person is using, stay the same through a single visit or interaction with your product. But other design conditions—like energy consumption, lighting, and signal strength—have the potential (and tendency) to change during the course of a single visit, or even from page load to page load.

Just a year ago, I wouldn’t have had much of an answer for these user experience problems because the device-level APIs needed weren’t ready for primetime yet. But today, we can start to do something to improve our users’ experiences, even under these dynamic conditions, thanks to the recent buildup of the Device API.

## What is the Device API?

The Device API started in July of 2011 when Mozilla and Dr. Andreas Gal created Boot2Gecko, an operating system entirely based on web technologies. The interesting piece to this OS is that Mozilla was also creating JavaScript APIs that allow device-level access from the browser.

Some of the APIs have stayed contained within the Boot2Gecko operating system, but a lot of the work has been transferred to the W3C for standardization. That’s the work we’ll be focusing on today as we explore these APIs and the potential they bring to improving how our products hold up against real-world and environmental design conditions.

## Battery Status and Network Information

Responsive design has saved us a lot of trouble. But it’s also brought new and exciting problems like asset management to the forefront. How do we deal with images in a way that scales to any situation, such as small screens or limited bandwidth?

If it were simply an issue of “small screens get small images,” the responsive images problem would pretty much be solved with the picture element. But this assumes a small screen should be served a smaller image to accommodate its size and potential bandwidth limitation. What we are starting to realize, though, is that the size of a display has very little relation to the amount of bandwidth available.

Under optimal conditions, everyone would have a lightning-fast connection with 100 percent battery life. The more people use mobile devices, the less likely that becomes, and the more often these conditions will affect your users’ experience. If a user is casually browsing over a fast connection, low-resolution images aren’t going to result in the best experience. On the other hand, if a user has a poor connection and minimal battery life, downloading enormous images could leave him with a dead phone.

It’s situations like this that make the Battery Status and Network Information APIs so interesting.

The Battery Status API can tell you how much battery life is left in the device (level), whether the level is going down (discharging) or whether the level is going up (charging). This information isn’t only provided as a snapshot at load time, but also at events that are tied to the battery status. The events that are currently in the specification include: onchargingchange, onchargingtimechange, ondischargingtimechange, and onlevelchange.

This gets a whole lot more interesting when coupled with the Network Information API, which lets you tap into bandwidth information about a device. As the draft is currently written, it returns two pieces of information: the connection speed in MB per second, and a true/false boolean value to inform you if the bandwidth is being metered in any way by the ISP. This is all the information you need to filter assets and manage bandwidth in the browser. To track when a user is offline, this API can also return a connection of 0.

Even though Network Information and Battery Status work wonders on their own, the combination of these two APIs has the potential to help you not just manage assets at initial page load, but also to modify the interface as the connection or battery status changes over time. You can even run energy tests to give a user an estimate about when her battery might die under the current conditions (like “miles to empty” in a car). You won’t be able to get specific information like “Facebook is draining your battery,” but you will know whether there’s enough energy to accomplish a certain task in your application.

These two APIs, and particularly the combination of them, should likely be our first resources for making designs better equipped to handle real-world scenarios. They allow us to detect for performance bottlenecks and craft an experience around them (remember our image management problem?). But there are a couple others that really stand out from the pack as well: the Ambient Light Sensor and Proximity Sensor APIs, which take experiences a little further out of the browser.

## Ambient Light Sensor

The Ambient Light Sensor API uses the light sensor of a device to tell us about its current environment. Of course, the limitation of this API is that the device needs to have a light sensor, whether it’s filtered through the camera or through another type or sensor. It doesn’t matter where the sensor is, but it does have to exist. The API functions in much the same way as Battery Status in that the light level can be captured at initial load time and also through an event called ondevicelight.

This API might feel a little weird because it doesn’t use a normal web value like pixel, percentage, or em; the API returns values in lux units (lx). A lux unit is an international measurement of light intensity—not something we typically use on the web. In fact, I’d never heard of a lux before I discovered this API, but it makes me feel super-smart when I bring it up. Because this is relatively cutting edge, the device-level support for a lux value is a little hit-and-miss.

The Ambient Light Sensor API would likely improve the experience of using an e-reader, like the Kindle, because it allows access to information about the available light in a room. With this information, you can easily adjust color values, typography, or other design elements to provide a more comfortable reading experience.

## Proximity Sensor

The Proximity Sensor API, which enables near field communication (NFC) from the browser, is probably the furthest from our reach today—not because the specification is behind, but rather because most devices don’t yet have the necessary sensors. Relatively few smartphones contain NFC technology right now, and it could be a couple more releases until we see it in something like the iPhone.

If the user’s device contains a proximity sensor, you can access it to detect nearby objects enabled with NFC information (awesome, right?). The API contains an event called ondeviceproximity, which is triggered when an object is within the range of the sensor.

The W3C doesn’t recommend trying to accurately measure the distance of an object due to the volatility of today’s sensors. But you can still push the limits of user experience with just a few keystrokes by removing yourself from the browser’s constricting environment and unleashing the real world of interactive objects, light sensitivity, connection information, and energy consumption into an interface.

## Pushing on with environmental design

Environmental design on the web is simply the concept of taking outside factors into account—something we’re just seeing the beginning of with the Device API.

More APIs are becoming available every day that you can start integrating into your applications in creative ways, but you shouldn’t feel limited by them, either. We know an experience doesn’t have to be the same in every browser, but I would argue it doesn’t necessarily have to be the same in every room of your house, either. As connections, battery life, and other situations change, so can a user’s experience with your site.

Dealing with chaos in the browser is a full-time job for most of us—it’s why we have quality assurance testing. The key to advancing the web and creating a successful experience is to embrace this chaos rather than spend your time fighting against it. Using the madness to your advantage and constantly adding to your UX tool belt will ensure we all help move web experience in the right direction.

