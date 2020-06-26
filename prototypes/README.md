# spatial-finance

Connecting smart contracts to satellite imagery and IoT data via analytics algorithms. Enclaves everywhere lol. 

A privacy-preserving autonomous incentive for pro-environmental results. 


Data source

Time series feeds from connected sensors. Initially, satellite imagery from multispectral earth observation sensors capable of detecting the visible spectrum and others required to derive greenhouse gas emissions. Also could accept any data structures from any source. Trusted IoT is important for this reason.

Vector polygons held at service endpoints of DID documents registered on a public blockchain.

A network of validator enclaves. These 
- decrypt and validate the integrity and authenticity of the image (tiff probably) and the vector feature (geojson), 
- clip the raster with the vectors, 
- then pass clipped rasters into analytics algorithms (even simple band math at first) that determines the level of emissions, or any other value that can be derived from a satellite image (% forest, maybe). 
- The enclave creates a transaction designated for a contract address, passing the output value as an argument. 
- The enclave signs the transaction with the private key and returns it (or even just sends it to the network). (Other parameters: time of image - or duration represented in the image?)

A contract is developed that holds funds and disburses on an interval based on the relative 'weight' of the image submitted.

Funds are disbursed to the beneficiary address designated in the geojson `properties` object in the service endpoint:

```javascript

const tx = {
    from: "0x1",
    to: "0x2",
    parameters: {
        weight: 0.32,
        duration: 143234224, // (number of blocks? milliseconds.)
    }
}

```

And solidity:

```javascript

// use as a require
function require(duration) {
    if (network.block > lastClaim + 200) { // something with duration too? Can only claim so often
        // this means they're eligible - this could be a require
        // calculate payment amount
        _;
    }
}

function assessChange(weight, duration, beneficiary) {

}
    

```

As 

Analytics algorithms 