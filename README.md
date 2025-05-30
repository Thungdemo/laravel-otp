# Laravel OTP
## Installation
Run composer
```
composer require thungdemo/laravel-otp
```
Publish config file
```
php artisan vendor:publish --provider="Thungdemo\LaravelOtp\Providers\OtpServiceProvider" --tag="laravel-otp"
```
## Usage
```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Thungdemo\LaravelOtp\Rules\OtpVerify;
use Otp;

class OtpController extends Controller
{
    /**
     * sending otp
     */
    public function generateOtp()
    {
        // generate otp against a key
        $code = Otp::generate('9236852397');
        
        // send otp sms or email here
    }
    
    /**
     * validating otp
     */
    public function validateOtp(Request $request)
    {
        //validate the sms otp
        $this->validate($request,[
            'otp' => [new OtpVerify('9236852397')],
        ]);
    }
}
