/**
 *  Reset Once a Day
 *
 *  Author: Brian Gudauskas
 *
 *  Reset Energy Meter once per day
 */

definition(
    name: "Reset Once a Day",
    namespace: "bridaus",
    author: "Brian Gudauskas",
    description: "Reset one or more energy meters at a specified time",
    category: "Convenience",
    iconUrl: "https://s3.amazonaws.com/smartapp-icons/Allstate/save_energy_save_money.png",
    iconX2Url: "https://s3.amazonaws.com/smartapp-icons/Allstate/save_energy_save_money@2x.png"
   
)

preferences {
	section("Select energy meters to reset...") {
		input name: "energyMeters", type: "capability.energyMeter", multiple: true
	}
	section("Reset them all at...") {
		input name: "startTime", title: "Reset Time?", type: "time"
	}
}

def installed() {
	log.debug "Installed with settings: ${settings}"
	schedule(startTime, "startTimerCallback")

}

def updated(settings) {
	unschedule()
	schedule(startTime, "startTimerCallback")
}

def startTimerCallback() {
	log.debug "Resetting Energy Meters..."
	energyMeters.reset()
}
