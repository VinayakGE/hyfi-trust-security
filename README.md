# // Hybrid Finance Security & Trust Contract (Minimal Example)
pragma solidity ^0.8.0;

contract HybridFinanceTrust {
    mapping(address => uint256) public trustScore;
    mapping(address => bool) public verifiedIdentity;

    event IdentityVerified(address indexed user, uint256 score);
    
    function verifyIdentity(address user, uint256 score) public {
        require(score <= 100, "Invalid Trust Score");
        trustScore[user] = score;
        verifiedIdentity[user] = true;
        emit IdentityVerified(user, score);
    }

    function getTrustScore(address user) public view returns (uint256) {
        return trustScore[user];
    }
}
