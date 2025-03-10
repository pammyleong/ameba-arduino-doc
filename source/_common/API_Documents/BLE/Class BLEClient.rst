Class BLEClient
===============

.. contents::
  :local:
  :depth: 2

**BLEClient Class**
-------------------

**Description**
~~~~~~~~~~~~~~~

A class used for discovering and accessing BLE GATT services on a connected remote device.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    class BLEClient

**Members**
~~~~~~~~~~~

+------------------------------------+------------------------------------+
| **Public Constructors**                                                 |
+====================================+====================================+
| No public constructor is available for this class. You can get a pointer|
| to an instance of this class using BLEDevice::addClient().              |
+------------------------------------+------------------------------------+
| **Public Methods**                                                      |
+------------------------------------+------------------------------------+
| BLEClient::connected               | Check if the remote device         |
|                                    | associated with the client is      |
|                                    | connected.                         |
+------------------------------------+------------------------------------+
| BLEClient::discoverServices        | Start service discovery process    |
|                                    | for connected device               |
+------------------------------------+------------------------------------+
| BLEClient::discoveryDone           | Determine if service discovery     |
|                                    | process has been completed         |
+------------------------------------+------------------------------------+
| BLEClient::printServices           | Format and print discovered        |
|                                    | services to serial port            |
+------------------------------------+------------------------------------+
| BLEClient::getService              | Get a service with the             |
|                                    | specified UUID on the remote       |
|                                    | device                             |
+------------------------------------+------------------------------------+
| BLEClient::getConnId               | Get connection ID corresponding    |
|                                    | to remote device                   |
+------------------------------------+------------------------------------+
| BLEClient::getClientId             | Get corresponding client ID        |
+------------------------------------+------------------------------------+
| BLEClient::setDisconnectCallback   | Set a user function to be          |
|                                    | called when the remote device      |
|                                    | is disconnected                    |
+------------------------------------+------------------------------------+

**BLEClient::connected**
------------------------

**Description**
~~~~~~~~~~~~~~~

Check if the remote device associated with the client is connected.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    bool connected(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

This function returns TRUE if the remote device is connected.

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "BLEClient.h" must be included to use the class function.

**BLEClient::discoverServices**
-------------------------------

**Description**
~~~~~~~~~~~~~~~

Start the service discovery process for the connected remote device.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void discoverServices(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

Example: `BLEUartClient <https://github.com/Ameba-AIoT/ameba-arduino-pro2/blob/dev/Arduino_package/hardware/libraries/BLE/examples/BLEUartClient/BLEUartClient.ino>`_

.. note :: "BLEClient.h" must be included to use the class function.

**BLEClient::discoveryDone**

**Description**
~~~~~~~~~~~~~~~

Determine if the service discovery process has been completed.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    bool discoveryDone(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

This function returns TRUE if the service discovery process has been completed successfully, FALSE if the service discovery process failed, is still in progress, or has yet to start.

**Example Code**
~~~~~~~~~~~~~~~~

Example: `BLEUartClient <https://github.com/Ameba-AIoT/ameba-arduino-pro2/blob/dev/Arduino_package/hardware/libraries/BLE/examples/BLEUartClient/BLEUartClient.ino>`_

.. note :: "BLEClient.h" must be included to use the class function.

**BLEClient::printServices**
----------------------------

**Description**
~~~~~~~~~~~~~~~

Print out a formatted list of discovered services to the serial port.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void printServices(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "BLEClient.h" must be included to use the class function.

**BLEClient::getService**
-------------------------

**Description**
~~~~~~~~~~~~~~~

Get a service with the specified UUID on the remote device.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    BLERemoteService* getService(const char* uuid);
    BLERemoteService* getService(BLEUUID uuid);

**Parameters**
~~~~~~~~~~~~~~

uuid: the desired service UUID, expressed as a character array or a BLEUUID object.

**Returns**
~~~~~~~~~~~

This function returns the discovered service as a BLERemoteService object pointer, otherwise nullptr is returned if a service with the UUID is not found.

**Example Code**
~~~~~~~~~~~~~~~~

Example: `BLEUartClient <https://github.com/Ameba-AIoT/ameba-arduino-pro2/blob/dev/Arduino_package/hardware/libraries/BLE/examples/BLEUartClient/BLEUartClient.ino>`_

.. note :: "BLEClient.h" must be included to use the class function.

**BLEClient::getConnId**
------------------------

**Description**
~~~~~~~~~~~~~~~

Get the connection ID associated with the remote device.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    uint8_t getConnId(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

This function returns the connection ID for the connected remote device.

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "BLEClient.h" must be included to use the class function.

**BLEClient::getClientId**
--------------------------

**Description**
~~~~~~~~~~~~~~~

Get the client ID for the BLEClient object.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    T_CLIENT_ID getClientId(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

This function returns the BLEClient object's client ID.

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: The client ID is used when calling internal GATT client API. "BLEClient.h" must be included to use the class function.

**BLEClient::setDisconnectCallback**
------------------------------------

**Description**
~~~~~~~~~~~~~~~

Set a user function as a callback function when the remote device is disconnected.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void setDisconnectCallback(void (*fCallback) (BLEClient* client));

**Parameters**
~~~~~~~~~~~~~~

fCallback: A user callback function that returns void and takes one argument.

client: A pointer to the BLEClient object corresponding to the disconnected remote device.

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: The user callback function will be called after the remote device has disconnected, before the characteristics, services and client associated with the remote device are deleted. "BLEClient.h" must be included to use the class function.
